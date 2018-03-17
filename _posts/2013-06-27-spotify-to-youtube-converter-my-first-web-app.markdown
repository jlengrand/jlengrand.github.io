---
layout: post
status: publish
published: true
title: ! 'Spotify to Youtube converter : My first web app'
author: Julien Lengrand-Lambert
author_login: jlengrand
author_email: julien@lengrand.fr
author_url: https://www.lengrand.fr
wordpress_id: 873
wordpress_url: https://www.lengrand.fr/?p=873
date: 2013-06-27 07:32:37.000000000 +02:00
categories:
- Uncategorized
- programming
tags:
- url
- programming
- spotify
- youtube
- converter
- web app
- spotify to youtube
- music
- node
comments: []
---
The past year, I have created <a title="ivolution" href="https://jlengrand.github.io/Ivolution/" target="_blank"><strong>my first piece of software</strong></a> from scratch. And I know that even though it is ugly and has no coverage at all (and doesn't deserve it) it works.

More lately, my<strong><a title="brestram" href="https://play.google.com/store/search?q=brestram&amp;c=apps" target="_blank"> first android application</a></strong> came out (it has reviews, but in french :)). I learnt a lot during this one, as it involved reverse engineering a POST Request based protocol and I had no knowledge about the Web concepts at all. In fact I didn't even know know what POST was :). And even though I have updated it only once since then, I have around <strong>270 active users</strong> and 2 to 8 more coming a day. (And people are really happy!)

Those last weeks, I have been working on <a title="spo2tu.be" href="https://spo2tu.be/" target="_blank"><strong>spo2tu.be</strong></a>, a simple <strong>spotify to youtube converter</strong> and could finally release it this week end. So I can officially say that I also created my first web app!
<h2>The concept is really simple:</h2>
<a title="spotify" href="spotify.com" target="_blank">Spotify</a> users can share songs via facebook. But I hate facebook, and I hate the facebook integration in other parties even more.

The other aternative is a http link. Thing is <strong>this link is only playable for spotify customers</strong>. And this is boring!

So comes<strong> spo2tu.be</strong>, that takes your spotify url and <strong>tranforms it into its best youtube equivalent</strong> so that you can share it with your friends without any problem!
I must say I am quite happy with the app, but it seems like I am the only one having this problem because<strong> the website had no traction at all</strong>, whether it be on<a title="hacker news" href="https://news.ycombinator.com" target="_blank"> hacker news</a> or <a title="reddit" href="reddit.com" target="_blank">reddit</a>.
What I am really thrilled about though, is that <strong>this was the first time I have scratched my own itch</strong>, and not someone else's. Since the app is up, I already used it 4 times a day to share songs.

As usual, I tried to do something I had no experience about at all, and it has been quite a mess.
<h2>But let's talk about the way the magic happens</h2>
Once you enter the spotify web url, spo2tu.be queries <a title="spotify's webplayer" href="open.spotify.com/track/6tY0fjwn04azpjHsQGbVtC" target="_blank">spotify's webplayer</a> and extracts the name of the song and the group from the page. I know I could have used the <a title="spotify API" href="https://developer.spotify.com/technologies/web-api/" target="_blank">api</a>, but I already had some experience of webscraping with <a title="Brestram" href="https://play.google.com/store/search?q=brestram&amp;c=apps" target="_blank">Brestram</a> and I didn't want to query the spotify api a lot with my own customer name.
Once the name of the song is known, I simply query the <a title="youtube API" href="https://developers.google.com/youtube/" target="_blank">youtube API</a> and retrieve the most likely candidate.
Finally, the server sends the results back to the client which display everything to the user.

This was the<strong> first client/server app</strong> I developed from scratch, so I spent quite some time trying to figure out how everything had to work :).
I wanted to get my hands of <strong><a title="node" href="https://nodejs.org/" target="_blank">node</a></strong> for a long time, so this was my requirements for this project (even though <a href="https://flask.pocoo.org/" target="_blank"><strong>Flask</strong></a> would have probably been simpler).
For the client side code, I decided to take <a href="https://backbonejs.org/" target="_blank"><strong>backbone</strong></a> as a basis. I wanted something low level, so that I could grasp as much concepts as possible. This is why I decided to avoid <a href="https://meteor.com/" target="_blank"><strong>meteor</strong></a>, for example.
I use <a href="https://twitter.github.io/bootstrap/" target="_blank"><strong>bootstrap</strong></a> for the rendering. I started with <a href="https://purecss.io/" target="_blank"><strong>purecss</strong></a>, but having no idea at all of what I was doing I backed up after a few hours to an easier choice.
I use <a href="https://www.mongodb.org/" target="_blank"><strong>mongodb</strong></a> in the server, which is really convenient because you can feed it with json objects directly.
<h2>I thing I said it all.</h2>
The first real difficulty for me was to understand the concepts behind node, and especially the <strong>asynchronous programming</strong> part. At the very beginning, it even made it difficult to understand the docs, because the prototypes of the methods looked strange!
But after a few hours everything started to feel easier. And I was more than happy to let go of the threads and other queues :).
I also had quite a lot of trouble setting up the server environment. I spent hours trying to understand ec2, to finally find my instances destroyed or my security groups lost for no reason (or at least I couldn't find them!). On top of that, I was quite scared about the whole automatic billing/scaling stuff so I decided to stop with that. I finally found <a title="digital ocean" href="https://www.digitalocean.com/" target="_blank"><strong>digitalocean</strong></a>, and everything became (way) easier!
Backbone and boostrap were <strong>easier to handle that I would have expected</strong>. Maybe it's not that difficult after all :).

If you put everything together, having to learn javascript, REST, css, backbone, node and hosting at the same time was quite challenging. <strong>I spent some time in front of a huge pile of knots</strong>, trying to understand which string to pull!

But the app is finally up, and I hope some people will find it and start using it. I don't plan on making anything special with it, but<strong> it is still cool when the stuff you build with your hands is useful to someone</strong> :).

<a title="spo2tube" href="https://spo2tu.be/" target="_blank"><strong>Now go and try it out :) </strong></a>
