---
layout: post
status: publish
published: true
title: ! 'Classification : Hu and Zernike moments'
author: Julien Lengrand-Lambert
author_login: jlengrand
author_email: julien@lengrand.fr
author_url: https://www.lengrand.fr
wordpress_id: 254
wordpress_url: https://www.lengrandlambert.fr/wordpress/?p=254
date: 2011-11-02 00:51:12.000000000 +01:00
categories:
- Computer Vision
- Matlab
tags:
- image processing
- hu
- zernike
- moments
- matlab
- classification
comments:
- id: 750
  author: Deniz Cicek
  author_email: zendeniz1@yahoo.com
  author_url: ''
  date: !binary |-
    MjAxMi0wMy0zMSAxMjowNjo0NiArMDIwMA==
  date_gmt: !binary |-
    MjAxMi0wMy0zMSAxMTowNjo0NiArMDIwMA==
  content: Thanks. The links those you shared, will help me very much. Have a nice
    day.
- id: 755
  author: Julien Lengrand-Lambert
  author_email: julien@lengrand.fr
  author_url: https://www.lengrand.fr
  date: !binary |-
    MjAxMi0wNC0wMiAwODowNzowOCArMDIwMA==
  date_gmt: !binary |-
    MjAxMi0wNC0wMiAwNzowNzowOCArMDIwMA==
  content: ! "Hi Deniz, \r\n\r\nGlad it helped ;), I searched for them a long time
    some years ago.\r\nFeel free to come back if you need some code using them :)."
- id: 974
  author: Mohammad
  author_email: bagheri@cs.dal.ca
  author_url: ''
  date: !binary |-
    MjAxMi0wNS0xMyAxODo0NzoyNSArMDIwMA==
  date_gmt: !binary |-
    MjAxMi0wNS0xMyAxNzo0NzoyNSArMDIwMA==
  content: ! "First, thank you so much for your post... But, regarding the Zernike
    code, I didn't understand how to get it, how to implement it ! \r\nDoes I need
    to download Matlab and C++ files separately and put them in a folder and then
    mex C files?\r\nThanks again"
- id: 1011
  author: Julien Lengrand-Lambert
  author_email: julien@lengrand.fr
  author_url: https://www.lengrand.fr
  date: !binary |-
    MjAxMi0wNS0yMSAxMzowNzoyNSArMDIwMA==
  date_gmt: !binary |-
    MjAxMi0wNS0yMSAxMjowNzoyNSArMDIwMA==
  content: ! "Hi Mohammad, \r\n\r\nSorry for the delay, I was in vacation. Did you
    succeed into using it ? \r\n\r\nI posted this code some time ago now, but I do
    recall having to compile it. \r\nIt seems weird for me to download each file separately
    though. \r\n\r\nLet me some time and I will try it and let you know :)"
---
Hi all,

I am currently working on a <strong>Computer Vision</strong> application which requires a step of <strong>shape recognition</strong>. And I have been searching for lots of different parameters allowing to precisely classify objects afterwards.

In a lot of applications, one need parameters that are invariant to <strong><a title="linear transformation" href="https://en.wikipedia.org/wiki/Linear_map" target="_blank">linear transformations</a></strong> (that is translation, rotation and scaling) to ease object <strong>classification</strong> in various conditions.

If you search for such parameters, you will quickly hear the name of <strong><a title="zernike moments" href="https://homepages.inf.ed.ac.uk/rbf/CVonline/LOCAL_COPIES/SHUTLER3/node11.html" target="_blank">Zernicke</a></strong> and <strong><a title="hu" href="https://en.wikipedia.org/wiki/Image_moment" target="_blank">Hu</a> </strong>moments.  Here are links to a <strong>Matlab</strong> implementation of those descriptors:
<ul>
	<li><strong><a href="https://murphylab.web.cmu.edu/publications/boland/thesis_all.html" target="_blank">Zernike</a></strong> applied to protein localization</li>
	<li><strong><a href="https://www.cc.gatech.edu/~kwatra/computer_vision/ocr/OCR.html" target="_blank">Hu</a> </strong>applied to <a title="ocr" href="https://en.wikipedia.org/wiki/Optical_character_recognition" target="_blank">OCR</a></li>
</ul>
<div id="post-body-5906015610342128589">

Have fun using it, but don't forget to mention their previous authors ;).

And if you need more descriptors in your classification, <a title="visual descriptors" href="https://en.wikipedia.org/wiki/Visual_descriptors" target="_blank"><strong>here is a quite exhaustive list</strong> </a>(at least as much as it can be).

If I have some spare time, I might think of a Pythonic implementation one day ^^. I'll let you know.

Hope you'll enjoy ;)

See You

</div>
