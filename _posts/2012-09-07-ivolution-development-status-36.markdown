---
layout: post
status: publish
published: true
title: Ivolution – Development status 36
author: Julien Lengrand-Lambert
author_login: jlengrand
author_email: julien@lengrand.fr
author_url: http://www.lengrand.fr
wordpress_id: 746
wordpress_url: http://www.lengrand.fr/?p=746
date: 2012-09-07 08:23:33.000000000 +02:00
categories:
- Python
- Ivolution
tags:
- github
- development
- face recognition
- timelapse
- everyday
- wxpython
comments: []
---
Below is an update of my progress on the <strong><a title="ivolution" href="http://github.com/jlengrand/FaceMovie" target="_blank">Ivolution</a> </strong>! As you can see, the software has never been so close to be released :)
<ul>
	<li>
<h2>Hunt for bugs and crashes</h2>
</li>
</ul>
I spent a lot of time the last week pushing buttons like crazy, having incoherent behaviour and testing whatever could crash the software.

It allowed me to find several ugly things, like a random crash on exit !

There is not much to say about it, but that the software is now more reliable and stable. Not sexy to say, but I'm sure users will be happy !
<ul>
	<li>
<h2>Add new notifications to the interface</h2>
</li>
</ul>
Test the software made me realize that some of the unexpected events where not reported to the user.<strong> There was nothing warning if the input folder was empty</strong> for example.

To solve that, I simply added new notifications to the interface. This way, the user can now that the software has not actually crashed !
<div></div>
<div></div>
<ul>
	<li>
<h2>Create a compressed installer for Windows</h2>
</li>
</ul>
<strong>My biggest achievement of this week has been to create a full installer for Windows. </strong>

Windows users now a once click install solution to use the <strong>Ivolution</strong>. It was more challenging than expected, as (of course) the installer behavior is different depending on the Windows version of the user. But the opposite would not be fun, would it ?  ;)

I especially struggled finding solutions for the uninstall script to be reliable, and also give access to the icons to the software.

But I am proud to say that the Ivolution now can be properly installed on a Windows machine, and the user is even given pretty shortcuts ! To create this installer I used <strong><a title="NSIS" href="http://www.winamp.com/" target="_blank">NSIS</a></strong>, a tool created by the developers of <strong><a title="winamp" href="http://www.winamp.com/" target="_blank">Winamp</a> </strong>(amongst other great software). And I must say I was impressed how simple it was to get a simple working example. I definitely recommend using it !

<a href="{{ site.url }}/images/posts/2012/09/00_ivolution_installer.png"><img class="size-full wp-image-748" title="00_ivolution_installer" src="{{ site.url }}/images/posts/2012/09/00_ivolution_installer.png" alt="Ivolution windows installer" width="763" height="543" /></a>

<h3>My objectives for next week:</h3>
<ul>
	<li><strong>Write a proper documentation/manual.</strong></li>
</ul>
<div>I can now say that I have a <a title="MVP" href="http://en.wikipedia.org/wiki/Minimum_viable_product" target="_blank"><strong>minimum viable product</strong></a>. The software runs and gives expected results, and It can be installed on both Windows and Linux.</div>
Now I need users !

But for that, I have to spend some time working <strong>on the documentation</strong> and present it nicely. I also need a homepage for the project. I think about registering to <a title="sourceforge" href="http://sourceforge.net/" target="_blank">SourceForge</a>.
<ul>
	<li><strong>Warn early users, get the product tested.</strong></li>
</ul>
<div></div>
Even though the interface is still not perfect, I think it is time for the product to be shipped. There is nothing better than users to kepp you motivated.

I don't present any other objectives today. My whole mind is turned towards product release.

So let's write this documentation !

<strong>To get the last version of the Ivolution,<a title="ivolution last" href="http://github.com/jlengrand/FaceMovie/tree/gui_v2" target="_blank"> </a><a title="Ivolution" href="http://github.com/jlengrand/FaceMovie" target="_blank">clone the github project</a>.</strong>
