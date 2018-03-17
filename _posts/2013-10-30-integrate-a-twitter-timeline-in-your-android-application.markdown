---
layout: post
status: publish
published: true
title: Integrate a twitter timeline in your android application.
author: Julien Lengrand-Lambert
author_login: jlengrand
author_email: julien@lengrand.fr
author_url: http://www.lengrand.fr
wordpress_id: 899
wordpress_url: http://www.lengrand.fr/?p=899
date: 2013-10-30 18:10:55.000000000 +01:00
categories:
- Uncategorized
- programming
tags:
- android
- brestram
- java
- twitter
- timeline
- social
comments: []
---
Hey all,

This week-end, I worked on integrating a social feature in <a title="brestram google play" href="http://play.google.com/store/apps/details?id=fr.lengrand.brestram&amp;hl=en"><strong>BresTram</strong></a>.
I needed a way to let the users know when the bibus servers have a problem, and also let users send messages to each others if needed.

Finally,<strong> I didn't want to spend too much time developing</strong> it. I have more pressing features to implement, and the social integration is more of a "test".
I decided to go with <strong>Twitter</strong>. The message will generally be short (work on the rails, problems with the tram, ...), and everybody should be able to see them.

I started looking at the <a title="twitter streaming api" href="http://dev.twitter.com/docs/streaming-apis" target="_blank">Streaming API</a>, but then realized there was a much simpler way to do it : Simply integrate a web <a title="twitter timelines" href="http://dev.twitter.com/docs/embedded-timelines" target="_blank">timeline</a> into my app.

I started by creating a dedicated filter on the twitter account of BresTram.

This gives me two lines of code to integrate into the website of my choice :

{% highlight html %}

<a class="twitter-timeline" href="http://twitter.com/search?q=%23BresTram" data-widget-id="394415351972114432">Tweets about "#BresTram"</a>
<script>!function(d,s,id){var js,fjs=d.getElementsByTagName(s)[0],p=/^http:/.test(d.location)?'http':'https';if(!d.getElementById(id)){js=d.createElement(s);js.id=id;js.src=p+"://platform.twitter.com/widgets.js";fjs.parentNode.insertBefore(js,fjs);}}(document,"script","twitter-wjs");</script>
{% endhighlight %}

Then, I simply created a new Activity in my Application, that contains a webview.

{% highlight java %}
package fr.lengrand.brestram;

import android.os.Bundle;
import android.support.v7.app.ActionBarActivity;
import android.view.Menu;
import android.view.MenuItem;
import android.webkit.WebView;

public class MainActivity extends ActionBarActivity {
     
    public static final String TAG = "TimeLineActivity";
 
    private static final String baseURl = "http://twitter.com";
 
    private static final String widgetInfo = "<a class=\"twitter-timeline\" href=\"http://twitter.com/search?q=%23BresTram\" data-widget-id=\"394415351972114432\">Tweets about \"#BresTram\"</a> " +
            "<script>!function(d,s,id){var js,fjs=d.getElementsByTagName(s)[0],p=/^http:/.test(d.location)?'http':'https';if(!d.getElementById(id)){js=d.createElement(s);js.id=id;js.src=p+\"://platform.twitter.com/widgets.js\";fjs.parentNode.insertBefore(js,fjs);}}(document,\"script\",\"twitter-wjs\");</script>";

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
 
        load_background_color();
 
        WebView webView = (WebView) findViewById(R.id.timeline_webview);
        webView.getSettings().setDomStorageEnabled(true);
        webView.getSettings().setJavaScriptEnabled(true);
        webView.loadDataWithBaseURL(baseURl, widgetInfo, "text/html", "UTF-8", null);
    }
 
 
    private void load_background_color() {
        WebView webView = (WebView) findViewById(R.id.timeline_webview);
        //webView.setBackgroundColor(getResources().getColor(R.color.twitter_dark));
        webView.setBackgroundColor(0); // transparent
    }
 
    @Override
    public boolean onCreateOptionsMenu(Menu menu) {
        return true;
    }
 
    @Override
    public boolean onOptionsItemSelected(MenuItem item) {
        return true;
    }
}

{% endhighlight %}

The background color method is needed to avoid the ugly white background behind the timeline. I use a transparent background in this case.
<strong>It is not possible to set the background directly in the xml layout for webviews; you will have to do it in the activity directly.</strong>

And here is the layout file :

{% highlight xml %}
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:paddingBottom="@dimen/activity_vertical_margin"
    android:paddingLeft="@dimen/activity_horizontal_margin"
    android:paddingRight="@dimen/activity_horizontal_margin"
    android:paddingTop="@dimen/activity_vertical_margin"
    tools:context=".TimeLineActivity" >

    <WebView
        android:id="@+id/timeline_webview"
        android:layout_width="fill_parent"
        android:layout_height="fill_parent"/>

</RelativeLayout>
{% endhighlight %}

I used fill_parent because I wanted to give as much space as possible to the Webview.

The last thing you want to do is make sure you are allowing your app to make web calls. For that, add this line in your Android Manifest.

{% highlight xml %}
<uses-permission android:name="android.permission.INTERNET" />
{% endhighlight %}

The result is far from perfect, but it's not that bad for roughly 30 minutes of work :).

<a href="{{ site.url }}/images/posts/2013/10/twitter_timeline.png"><img class="size-full wp-image-900" alt="twitter timeline embedded into an android application" src="{{ site.url }}/images/posts/2013/10/twitter_timeline.png" width="480" height="800" /></a>

On top of that, It directly allows my users to post tweets from the application (using the timeline), and will let everybody know about the <a title="BresTram twitter account" href="http://twitter.com/BresTramApp" target="_blank">BresTram twitter account</a>.
Hopefully, this will help me get some useful feedback.

Now, back to more complex features :).
<strong>Oh, and if you leave near Brest, check out <a title="brestram google play" href="http://play.google.com/store/apps/details?id=fr.lengrand.brestram&amp;hl=en" target="_blank">BresTram</a>!</strong>

<em>P.S: This is not exactly how the actual source code look like. I changed several things to highlight the essentials in this post.</em>

<em>EDIT : Edited after a request on 28th Feb. 2015.</em>