---
layout: post
status: publish
published: true
title: Playing around with Google Maps and Puppeteer to track parking lots
author: Julien Lengrand-Lambert
author_login: jlengrand
author_email: julien@lengrand.fr
author_url: http://www.lengrand.fr
categories:
- work
- job
- development
tags:
- javascript
- node
- experiment
- google maps
- ing
- work
- startup
- geomarketing
comments: []
---

Over the last weeks, I have been reading quite a bit about **[Geomarketing](https://en.wikipedia.org/wiki/Geomarketing)** and have been searching for fun experiements to do.
One of my ideas was to check how many of the largest [Carrefours](https://www.carrefour.fr/) in France has open parking lots in France. 

It was the perfect use case to start playing around with [Puppeteer](https://github.com/GoogleChrome/puppeteer), a **Headless Chrome Node API** I heard about for the first time at the Polymer Summit in Copenhagen last year.

The first thing to do was to gather all carrefour locations in a database. Luckily, the main website itself [has us covered](http://www.carrefour.fr/magasin/liste-carrefour).

The main idea is to check the list and extract the shop name as well as its location (coming from the Google Maps link).

## First steps 

I first tried simply with [BeautifulSoup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/), and [Selenium](Selenium - Web Browser Automation) but the website returned errors. Anti scraping protection!
I decided to switch to Puppeteer.

My first attempt was unsuccessful. Same error as for the other methods. 
The code is insanely concise though: 

```javascript
const puppeteer = require('puppeteer');

async function run() {
  const STORE_LINK_SELECTOR = ".k4-storelist-sublist-link"
  const CARREFOUR_BASE = "http://www.carrefour.fr/magasin/liste-carrefour";
  const browser = await puppeteer.launch({});
  const page = await browser.newPage();
  await page.goto(CARREFOUR_BASE);
  const linksArray = await page.evaluate(
    () => [...document.querySelectorAll('.k4-storelist-sublist-link')].map(elem => elem.href)
  );

  browser.close();
}

run();
```

The cool thing about Puppeteer is that you are actually manipulating Chrome, so you're not a robot per se (and you are gentle with the target's website).

The solution here was to remove the **headless** default. I like this, because the idea is not to suck the website dry but to extract some information that you could also get by hand.

```javascript
const browser = await puppeteer.launch({
    headless: false
});
```

Bingo! I can now gather the list of all shops webpage!

The next step was naturally to extract a latitude/longitude for each shop, together with a 'unique id' (name) per Carrefour. We iterate through the list of links found above, The core of the code can be contained in a single function

```javascript
async function getLocation(link, browser){
    const page = await browser.newPage();
    await page.goto(link);

    const title = await page.evaluate(() => document.querySelector(".k5-pagehead_storename").textContent);
    const location = await page.evaluate(() => document.querySelector("div.k5-pagehead_bottom > a:nth-child(1)").href);
    const url = queryString.parseUrl(location);
    const latlon = stringToLatLon(url.query.daddr);

    page.close();
}
```

In essence, what we do here is find the **Google Maps** link available for each of the shops' webpage and extract the lat/lon value using [querystring](https://www.npmjs.com/package/query-string).

Alright cool, we have all carrefours in France, with their exact location. What's next? Getting a bird's eye view of the location!

Here is the first version. Again, we run without the headless mode on to be gentle.

```javascript
async function makeScreenshot(location, browser){
    const title = location.title;
    const link = location.location;

    const page = await browser.newPage();
    await page.goto(link);
    
    await page.screenshot({ path: `screenshots/${title}.png` });
}
```

Here the location is a simple object containing a title (the name of the shop), as well as a Google Maps URL in the format https://maps.google.fr/?daddr=50.637,2.412.


## Solving issues

Though it's a good start, there are several little issues with the current version.

### Screenshots and Network

First, the screenshot might get taken before the Google Maps tiles are fully loaded. But as usual, Puppeteer has us covered and we can tell him to wait until there is no more network activity!

```javascript 
await page.goto(link, {"waitUntil" : "networkidle0"});
```
### Anonymous Chrome user 

Secondly, because we run a non logged in Chrome, the screenshot of Google Maps contains the cookie disclaimer as well as some **'do you want to opt-in for ...'** popups.

![Here is an example]({{ "/images/2018-04-05-puppeteer-google-maps-carrefour-google-popups.png" | absolute_url }})

We solve this by looking a bit in the DOM and clicking on those popups. You probably also can use existing cookies for your Chrome session, but I wanted to go the quick route :).

```javascript
//Removing popups
...
await page.click(".widget-consent-button-later");
await page.click(".section-homepage-promo-text-button");
...
```

Another catch with this is that past the first page, the privacy pop-up might not show any more. To solve this, I simply check if the element exists before trying to click on it :

```javascript
async function clickIfExists(thePage, selector){
    if (!!(await thePage.$(selector))){
        await thePage.click(selector);
    }
}
...
clickIfExists(page, ".widget-consent-button-later");
clickIfExists(page, ".section-homepage-promo-text-button");
...
```

### Tweaking the Google Maps view 

The last gotcha is that the default view for google maps is a 'map' view. I wanted a sattelite view! And I also wanted to control the zoom level of the view so I can see the cars on the parking lot. To do this, I fiddled around a found the corresponding Google Maps options.
The zoom level is being controlled using "z=level" in the query, and the type of map using the "t=type" option, with sattelite being "k" (go figure). This gives us the following handy method

```javascript
function transformUrl(link){
    // https://maps.google.fr/?daddr=50.637,2.412 to https://maps.google.fr/?ll=50.637,2.412&z=16&t=k

    return link.replace("daddr=", "ll=") + "&z=16&t=k";
}
```

Once this is all done, our tool is ready and we can run it. Seeing it find all locations is beautiful!


**[Check out a short video of the script running here](https://photos.app.goo.gl/Bq5DUnWOH6HfFSoa2)**

## Adding related Sentinel images

Google Maps is great, but it gives us only a snapshot and I have no idea when new images will come up. In order to be able to look into changes, I want to look into Satellite data feeds that are openly available.
The latest on my list was **[Sentinel 2](https://en.wikipedia.org/wiki/Sentinel-2)** with its 10 meters resolution, and 7 days passover time.

In order to find relevant images for a given location, I need to transform lat/lon coordinates into the **[Military Grid Reference System](https://en.wikipedia.org/wiki/Military_Grid_Reference_System)**.
This can relatively easily be done using a library called [usng.js](https://github.com/codice/usng.js/).

For a given location, we can use the following snippet to retrieve MGRS coordinates

```javascript
const usng = require('usng/usng.js');
const precision = 1;
const converter = new usng.Converter();
const mgrsCoord = converter.LLtoMGRS(lat, lon, precision);
console.log(mgrsCoord); //30TXT
```

Finally, in order to get relevant images, we can couple these new coordinates with the [open Sentinel datafeed on AWS](https://aws.amazon.com/public-datasets/sentinel-2/), which is conveniently in REST format.
To ge a URL, we can do something like

```javascript
const sentinelFeed = `http://sentinel-s2-l1c.s3-website.eu-central-1.amazonaws.com/#tiles/${mgrsCoord.substring(0, 2)}/${mgrsCoord.substring(2, 3)}/${mgrsCoord.substring(3)}/`;
```

## Next steps

Finally, I have coupled all those results in a database. There are only 324 results so a great simple tool like [lowdb](https://github.com/typicode/lowdb) will do wonders.
And to make browsing easy, I have added a very crude index.html file that shows up al data gathered. That will help further find which Sentinel data and locations I want to look into first.

You can see the file [here](https://jlengrand.gitlab.io/carrefour) (Careful though, the file is 300Mb big, there are a lot of screenshots in there!). 

## The end

You can check the complete code [here](https://gitlab.com/jlengrand/carrefour). It's not the most beautiful ever, as it is meant to run only once. But it gets the job done!

I hope you enjoyed this sneak peak in my last Friday night :).