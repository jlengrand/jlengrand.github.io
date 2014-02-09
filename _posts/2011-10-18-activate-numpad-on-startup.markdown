---
layout: post
status: publish
published: true
title: Activate numpad on startup
author: Julien Lengrand-Lambert
author_login: jlengrand
author_email: julien@lengrand.fr
author_url: http://www.lengrand.fr
wordpress_id: 29
wordpress_url: http://www.lengrandlambert.fr/wordpress/?p=29
date: 2011-10-18 13:14:24.000000000 +02:00
categories:
- tips
tags:
- numpad
- startup
- activate
comments:
- id: 7643
  author: elchusco
  author_email: elchusco12du63@gmail.com
  author_url: ''
  date: !binary |-
    MjAxMy0wNC0wNCAxMzowNDoxNyArMDIwMA==
  date_gmt: !binary |-
    MjAxMy0wNC0wNCAxMjowNDoxNyArMDIwMA==
  content: ! "Hi!\r\nI know this is an old post but i noticed that today, april 2013,
    the command numlock isn't included inthe numlockx package. So I used the numlockx
    cmd in the autostart SH script. I don't know if it was a mistake, but i'd like
    to correct it. \r\nHowever, thanks for this tips..."
- id: 8422
  author: Julien Lengrand-Lambert
  author_email: julien@lengrand.fr
  author_url: http://www.lengrand.fr
  date: !binary |-
    MjAxMy0wNC0xMSAwOToyNTo0MSArMDIwMA==
  date_gmt: !binary |-
    MjAxMy0wNC0xMSAwODoyNTo0MSArMDIwMA==
  content: ! "hey, \r\n\r\nThanks for letting me know. \r\nI'll check that next time
    I boot my Linux machine :). \r\n\r\nWhich distro are you running on ?"
- id: 10188
  author: Fabian
  author_email: hello@fabianpeter.de
  author_url: http://fabianpeter.de
  date: !binary |-
    MjAxMy0wNS0wNyAwODoxNjoxOSArMDIwMA==
  date_gmt: !binary |-
    MjAxMy0wNS0wNyAwNzoxNjoxOSArMDIwMA==
  content: Just tried this. After installing "numlockx", the correct command on Crunchbang
    (debian wheezy) is "numlockx on/off/toggle" :)
- id: 10417
  author: Julien Lengrand-Lambert
  author_email: julien@lengrand.fr
  author_url: http://www.lengrand.fr
  date: !binary |-
    MjAxMy0wNS0xMCAxOToxNDowMSArMDIwMA==
  date_gmt: !binary |-
    MjAxMy0wNS0xMCAxODoxNDowMSArMDIwMA==
  content: ! "Hey!\r\n\r\nThanks for the feedback. It is more than likely that you´re
    right, this post is old and I haven´t used Linux in while!\r\n\r\nI´ll check that
    on my next install :)"
---
Hi all,

I recently switched from Ubuntu to Crunchbang as main distribution for my home computer and I may even talk a bit more about it in a later post ;)

The main topic here is that my num pad wad not activated by default on boot, and I had to tap Verr. Num on each login. My password  having numbers, it quickly became quite boring . . .

Running Ubuntu, the solution was quite simple  : installing the numlockx package from the main repository.

Gaving Debian now, I tried the same :

[bash]
$sudo apt-get install numlockx
[/bash]

The package did install actually, but seems like it was not enough. . .

To run on startup, this module had to be added to the list of apps to be started <strong>after</strong> the X server .

On my Openbox based Crunchbang, the solution was to edit my autostart.sh to add a new line :

[bash]
$ echo &quot;(sleep 5s &amp;&amp; numlock) &amp;&quot; \
&gt;&gt; ~/.config/openbox/autostart.sh
[/bash]

<div>That's all !</div>
<div>CU</div>
<div><strong>Julien</strong></div>
