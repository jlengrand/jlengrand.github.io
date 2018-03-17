---
layout: post
status: publish
published: true
title: Converting a flv file to avi
author: Julien Lengrand-Lambert
author_login: jlengrand
author_email: julien@lengrand.fr
author_url: https://www.lengrand.fr
wordpress_id: 31
wordpress_url: https://www.lengrandlambert.fr/wordpress/?p=31
date: 2011-10-18 13:16:00.000000000 +02:00
categories:
- tips
tags:
- flv
- avi
comments: []
---
<em>This article was originally written on 1st July, 2010 in my previous blog.</em>

When working on slide presentations, it might be useful to insert one or two small videso that illustrates your words.

Most of my videso come from media websites, such as youtube, dailymotion, . . ..

Problem is, some of the compression formats are not quite usual and it might be difficult to read them easily.

Here is a small tip to convert a flv file to avi, which is mainly supported on all OSes.

This tip is useful for Linux users only ;)

First of all, install the <strong>ffmpeg</strong> package. All debian based distros can do the following. For the others, look at your package manager possibilities, or check for <a href="https://ffmpeg.org/download.html">sources</a>.

{% highlight bash %}
$ sudo apt-get install ffmpeg
{% endhighlight %}

Now, convert the video, replacing the argument to fit with your flv file.

{% highlight bash %}
$ ffmpeg -o /your/flv/file.flv -vcodec mpeg1-video \
 -acodec copy -ar 44100 -s 320x240 -y /your/avi/file.avi
{% endhighlight %}

For more information, check at <a href="https://pwet.fr/man/linux/commandes/ffmpeg">ffmpeg man page</a> ;)

&nbsp;

C U ;)

<strong>Julien</strong>
