---
layout: post
status: publish
published: true
title: Errors on Linux boot with a Radeon HD
author: Julien Lengrand-Lambert
author_login: jlengrand
author_email: julien@lengrand.fr
author_url: http://www.lengrand.fr
wordpress_id: 274
wordpress_url: http://www.lengrandlambert.fr/wordpress/?p=274
date: 2011-11-09 12:29:24.000000000 +01:00
categories:
- misc
tags:
- radeon
- radeon hd
- gem object
- ati
- amd
- debian
- GEM
- GPU
comments:
- id: 102
  author: The Don
  author_email: lengrand.fr@dontheduck.co.uk
  author_url: ''
  date: !binary |-
    MjAxMS0xMi0xOCAwNjowMDozMiArMDEwMA==
  date_gmt: !binary |-
    MjAxMS0xMi0xOCAwNTowMDozMiArMDEwMA==
  content: ! "Nice one, thankyou very much.\r\nMy problem was that after installing
    CrunchBang, on first boot, I had the same situation, but it kept scrolling the
    screen with the error message for more than 5 minutes before I reset the machine.\r\nBooted
    in recovery and removed 'plymouth' and the machine then proceeded to the login
    screen.\r\nMy card is a Radeon HD 5750\r\n\r\nDonald"
- id: 198
  author: Julien Lengrand-Lambert
  author_email: julien@lengrand.fr
  author_url: http://www.lengrand.fr
  date: !binary |-
    MjAxMi0wMS0zMCAxODoyODoxMCArMDEwMA==
  date_gmt: !binary |-
    MjAxMi0wMS0zMCAxNzoyODoxMCArMDEwMA==
  content: ! "Cool to see that the message helped someone else ;). \n\nStill couldn't
    find a good way to get plymouth working though :s."
---
Hi all,

For the past months, I had a huge issue with My <strong>debian</strong> based system.

I got a  Radeon 5770 graphical card and here are some more information:

[bash]
[airballman@crunchbang:~]$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Juniper [Radeon HD 5700 Series]
[/bash]

On startup, I would have 15/20 seconds of errors flooding my boot screen.

Here is the Error log, repeated again and again:

[bash]

[drm:radeon_ttm_backend_bind] *ERROR* failed to bind 1 pages at 0x0040F000
[TTM] Couldn't bind backend.
radeon 0000:01:00.0: object_init failed for (4096, 0x00000002)
[drm:radeon_gem_object_create] *ERROR* Failed to allocate GEM object (4096, 2, 4096, -22)

[/bash]

The problem as quite annoying, even causing<strong> graphical startup failures</strong>. . . I searched a lot for a solution and <a title="cr-fr" href="http://crunchbanglinux-fr.org/forum/viewtopic.php?id=1123" target="_blank">asked for some help</a>.

I tried lots of stuff, from installing new free drivers to the proprietary <strong>ati</strong> solution. The latter solved the problem, but caused<strong> mouse freezes</strong>. . .

After a lot of problems, <a title="darth" href="https://plus.google.com/109434034494027454595" target="_blank">DarthWound</a> finally gave my the good way to solve it !

The problem was coming from <strong><a title="plymouth" href="http://en.wikipedia.org/wiki/Plymouth_(software)" target="_blank">Plymouth</a></strong>, and removing it would remove the error :

[bash]

$ sudo apt-get remove plymouth

[/bash]

The con of this method is that you will lose your beautiful startup image. . .

Let me know if you find a better solution !

You may see the effect on my screen here :

<strong><a href="http://www.youtube.com/watch?v=btXGpa-pqGM">Gem Object problems on boot </a></strong>

<strong>C U </strong>
