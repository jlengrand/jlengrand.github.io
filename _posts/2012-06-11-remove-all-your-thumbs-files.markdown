---
layout: post
status: publish
published: true
title: Remove all your Thumbs files
author: Julien Lengrand-Lambert
author_login: jlengrand
author_email: julien@lengrand.fr
author_url: http://www.lengrand.fr
wordpress_id: 646
wordpress_url: http://www.lengrand.fr/?p=646
date: 2012-06-11 11:27:30.000000000 +02:00
categories:
- tips
tags:
- windows
- ubuntu
- thmbs
- thumbmails
- unix
- linux
- remove
- clean
comments: []
---
You too may have enjoyed Windows and its tendency to hide <a title="thumbs files" href="http://en.wikipedia.org/wiki/Windows_thumbnail_cache" target="_blank">Thumbs files</a> in any folder containing media files.

Basically, Windows creates those files to let you see <a title="thumbnail" href="https://en.wikipedia.org/wiki/Thumbnail" target="_blank">thumbnails</a> when you browse from file to file (or folder to folder . . . ).

And <strong><a title="why Linux is better" href="http://www.whylinuxisbetter.net/" target="_blank">as you now run Linux,</a></strong> those files are completely useless for you !

So here is the magic solution to get rid of those parasites :

{% highlight bash %}

$ sudo find any_folder -name "Thumbs.db" -exec rm {} \;

{% endhighlight %}

<em>any_folder</em> being of course the location you want to sanitize.

&nbsp;

You can now enjoy a world (slighlty) cleaner :).
