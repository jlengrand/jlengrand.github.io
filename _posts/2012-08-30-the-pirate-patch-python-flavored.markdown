---
layout: post
status: publish
published: true
title: The Pirate Patch, Python Flavored
author: Julien Lengrand-Lambert
author_login: jlengrand
author_email: julien@lengrand.fr
author_url: http://www.lengrand.fr
wordpress_id: 723
wordpress_url: http://www.lengrand.fr/?p=723
date: 2012-08-30 12:54:19.000000000 +02:00
categories:
- tips
- Python
tags:
- software
- development
- pirate bay
- piratebay
- os
comments:
- id: 1986
  author: Ivolution &#8211; Development status 35 | loup2fu
  author_email: ''
  author_url: http://www.lengrand.fr/2012/08/ivolution-development-status-35/
  date: !binary |-
    MjAxMi0wOC0zMSAxMjo1OTowOCArMDIwMA==
  date_gmt: !binary |-
    MjAxMi0wOC0zMSAxMTo1OTowOCArMDIwMA==
  content: ! '[...] Post navigation &larr; Previous [...]'
- id: 18724
  author: http://okaysorry.tumblr.com/
  author_email: solomon.farncomb@hotmail.de
  author_url: http://okaysorry.tumblr.com/post/61581328505/plants-against-zombies-2-cheats-most-important-tips
  date: !binary |-
    MjAxMy0xMC0xOCAyMjoxMjoyNCArMDIwMA==
  date_gmt: !binary |-
    MjAxMy0xMC0xOCAyMToxMjoyNCArMDIwMA==
  content: ! "Have you ever considered creating an ebook or guest authoring on other
    blogs?\r\nI have a blog based on the same ideas you discuss and would love to
    \r\nhave you share some stories/information. I know my \r\nreaders would value
    your work. If you are even remotely interested, feel free to send me an e mail."
---
Some of you might already have heard about <strong><a title="the pirate patch" href="http://elite.so/tpp/" target="_blank">The Pirate Patch</a></strong> (at least those who read <strong><a title="korben" href="http://korben.info/le-pirate-patch.html" target="_blank">Korben</a></strong>).

For several months now, the pirate bay is <a title="piratebay blocked" href="http://www.t-mobile.nl/sorry" target="_blank">blocked in several countries such as Belgium or the Netherlands</a>.
<strong>Qarizma</strong>, a member of the <strong><a title="elite.so" href="http://elite.so/" target="_blank">elite.so</a></strong> website has developed a small utility to get around this problem. The script uses reverse-proxy on some of the mirrors of the pirate bay that are not blocked. Basically, it simply modified your host file.

I downloaded the patch and wanted to give it a try. But it is developed in <a title="windows shell" href="https://en.wikipedia.org/wiki/Shell_(computing)" target="_blank">windows shell</a> and thus is <strong>only Windows compatible.</strong>

So last night, I simply looked at the source and developed <strong><a title="piratepatch in Python" href="https://gist.github.com/334576c898c0cd727075" target="_blank">a Python equivalent</a></strong>. This way everybody with a Python interpreter should be able to use it.

I packaged it into an executable and tried it successfully on Windows and Linux. I wait this week-end to get access to a Mac and be sure it works on all OSes.

If so, you may find it soon next to the windows version, on the <a title="elite.so" href="http://elite.so/" target="_blank">elite.so</a> website.
Hope this will help some of you :)
