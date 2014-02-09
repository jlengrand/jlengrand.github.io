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

This week-end, I worked on integrating a social feature in <a title="brestram google play" href="https://play.google.com/store/apps/details?id=fr.lengrand.brestram&amp;hl=en"><strong>BresTram</strong></a>.
I needed a way to let the users know when the bibus servers have a problem, and also let users send messages to each others if needed.

Finally,<strong> I didn't want to spend too much time developing</strong> it. I have more pressing features to implement, and the social integration is more of a "test".
I decided to go with <strong>Twitter</strong>. The message will generally be short (work on the rails, problems with the tram, ...), and everybody should be able to see them.

I started looking at the <a title="twitter streaming api" href="https://dev.twitter.com/docs/streaming-apis" target="_blank">Streaming API</a>, but then realized there was a much simpler way to do it : Simply integrate a web <a title="twitter timelines" href="https://dev.twitter.com/docs/embedded-timelines" target="_blank">timeline</a> into my app.

I started by creating a dedicated filter on the twitter account of BresTram.

This gives me two lines of code to integrate into the website of my choice :

[html]
&lt;a class=&quot;twitter-timeline&quot; href=&quot;https://twitter.com/search?q=%23BresTram&quot; data-widget-id=&quot;394415351972114432&quot;&gt;Tweets about &quot;#BresTram&quot;&lt;/a&gt;
&lt;script&gt;!function(d,s,id){var js,fjs=d.getElementsByTagName(s)[0],p=/^http:/.test(d.location)?'http':'https';if(!d.getElementById(id)){js=d.createElement(s);js.id=id;js.src=p+&quot;://platform.twitter.com/widgets.js&quot;;fjs.parentNode.insertBefore(js,fjs);}}(document,&quot;script&quot;,&quot;twitter-wjs&quot;);&lt;/script&gt;
[/html]

Then, I simply created a new Activity in my Application, that contains a webview.

[java]
package fr.lengrand.brestram;

import fr.lengrand.brestram.activities.BaseActivity;
import android.os.Bundle;
import android.webkit.WebView;

public class TimeLineActivity extends BaseActivity {
    public static final String TAG = &quot;TimeLineActivity&quot;;

    private static final String baseURl = &quot;https://twitter.com&quot;;

    private static final String widgetInfo = &quot;&lt;a class=\&quot;twitter-timeline\&quot; href=\&quot;https://twitter.com/search?q=%23BresTram\&quot; data-widget-id=\&quot;394415351972114432\&quot;&gt;Tweets about \&quot;#BresTram\&quot;&lt;/a&gt; &quot; +
            &quot;&lt;script&gt;!function(d,s,id){var js,fjs=d.getElementsByTagName(s)[0],p=/^http:/.test(d.location)?'http':'https';if(!d.getElementById(id)){js=d.createElement(s);js.id=id;js.src=p+\&quot;://platform.twitter.com/widgets.js\&quot;;fjs.parentNode.insertBefore(js,fjs);}}(document,\&quot;script\&quot;,\&quot;twitter-wjs\&quot;);&lt;/script&gt;&quot;;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_timeline);

        load_background_color();

        WebView webView = (WebView) findViewById(R.id.timeline_webview);
        webView.getSettings().setDomStorageEnabled(true);
        webView.getSettings().setJavaScriptEnabled(true);

        webView.loadDataWithBaseURL(baseURl, widgetInfo, &quot;text/html&quot;, &quot;UTF-8&quot;, null);
    }

    /**
     * Needed because android:background does not work
     * for WebViews
     */
    private void load_background_color() {
        WebView webView = (WebView) findViewById(R.id.timeline_webview);
        //webView.setBackgroundColor(getResources().getColor(R.color.twitter_dark));
        webView.setBackgroundColor(0); // transparent
    }
}

[/java]

The background color method is needed to avoid the ugly white background behind the timeline. I use a transparent background in this case.
<strong>It is not possible to set the background directly in the xml layout for webviews; you will have to do it in the activity directly.</strong>

And here is the layout file :

[xml]
&lt;RelativeLayout xmlns:android=&quot;http://schemas.android.com/apk/res/android&quot;
    xmlns:tools=&quot;http://schemas.android.com/tools&quot;
    android:layout_width=&quot;match_parent&quot;
    android:layout_height=&quot;match_parent&quot;
    android:paddingBottom=&quot;@dimen/activity_vertical_margin&quot;
    android:paddingLeft=&quot;@dimen/activity_horizontal_margin&quot;
    android:paddingRight=&quot;@dimen/activity_horizontal_margin&quot;
    android:paddingTop=&quot;@dimen/activity_vertical_margin&quot;
    tools:context=&quot;.TimeLineActivity&quot; &gt;

    &lt;WebView
        android:id=&quot;@+id/timeline_webview&quot;
        android:layout_width=&quot;fill_parent&quot;
        android:layout_height=&quot;fill_parent&quot;/&gt;

&lt;/RelativeLayout&gt;
[/xml]

I used fill_parent because I wanted to give as much space as possible to the Webview.

The result is far from perfect, but it's not that bad for roughly 30 minutes of work :).

[caption id="attachment_900" align="aligncenter" width="480"]<a href="http://www.lengrand.fr/wp-content/uploads/2013/10/twitter_timeline.png"><img class="size-full wp-image-900" alt="twitter timeline embedded into an android application" src="http://www.lengrand.fr/wp-content/uploads/2013/10/twitter_timeline.png" width="480" height="800" /></a> twitter timeline embedded into an android application[/caption]

On top of that, It directly allows my users to post tweets from the application (using the timeline), and will let everybody know about the <a title="BresTram twitter account" href="https://twitter.com/BresTramApp" target="_blank">BresTram twitter account</a>.
Hopefully, this will help me get some useful feedback.

Now, back to more complex features :).
<strong>Oh, and if you leave near Brest, check out <a title="brestram google play" href="https://play.google.com/store/apps/details?id=fr.lengrand.brestram&amp;hl=en" target="_blank">BresTram</a>!</strong>

<em>P.S: This is not exactly how the actual source code look like. I changed several things to highlight the essentials in this post.</em>
