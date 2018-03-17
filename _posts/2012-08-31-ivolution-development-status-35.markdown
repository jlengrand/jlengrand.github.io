---
layout: post
status: publish
published: true
title: Ivolution - Development status 35
author: Julien Lengrand-Lambert
author_login: jlengrand
author_email: julien@lengrand.fr
author_url: https://www.lengrand.fr
wordpress_id: 730
wordpress_url: https://www.lengrand.fr/?p=730
date: 2012-08-31 12:59:41.000000000 +02:00
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
Here is my weekly post about the status of the <strong><a title="ivolution" href="https://jlengrand.github.com/FaceMovie/" target="_blank">Ivolution</a></strong>.

During these last days, I have mostly been working on<a title="The Pirate Patch, Python Flavored" href="https://www.lengrand.fr/2012/08/the-pirate-patch-python-flavored/" target="_blank"> another project</a>. But at the same time, I also progressed like crazy on Ivolution !
So here are the news :
<ul>
	<li>
<h2><strong>Windows portability.</strong></h2>
</li>
</ul>
I have switched my main dev environement<strong> from Linux to Windows.</strong> This to ensure that my codebase is <strong>OS independant</strong> and to try to find new bugs. Up to know, everything went fine and I must say I am surprised things are going so well.
<ul>
	<li>
<h2><strong>New user interface.</strong></h2>
</li>
</ul>
Originally, I developed my GUI in pyGTK and was running it under Linux. But the framework is not windows compatible yet, and I want my application to run on everything. Plus I was not happy with the style of the GUI, and wanted something more interacting with the user.

<strong>So I redeveloped a new interface from scratch, this time using wxPython.</strong> Here is what it looks like right now :

<center><a href="{{ site.url }}/images/posts/2012/08/ivolution_29_08.png"><img class=" wp-image-731 " title="ivolution_29_08" src="{{ site.url }}/images/posts/2012/08/ivolution_29_08.png" alt="New gui of ivolution" width="337" height="391" /></a></center>

It is still really raw, and some of the menus are not implemented yet. But I find it <strong>way simpler and catchy</strong> than the old one.
<ul>
	<li>
<h2><strong>Real-time notifications on the interface</strong>.</h2>
</li>
</ul>
The most time consuming part of the Ivolution is definitely the <strong>face detection part</strong>. One must expect a 1 to 4 secondes processing time for each image, depending on its size. I wanted the user to be aware of that, while showing him that progress were made when he waits.

The last feature I developed is the centre panel of the application. When the algorithm runs, a list of al the images found is displayed. As they are processed, their color change:
a green font if the image contains faces, and a red font otherwise.
I am really happy of this, because now <strong>the user knows in real-time how the agorithm performs</strong>, and does not only wait for the end of the processing.
<ul>
	<li>
<h2><strong>Multi-OS parameters.</strong></h2>
</li>
</ul>
I also added an <strong>OS detection feature</strong>, to give correct default parameters. On startup, the Ivolution will detect the OS you are running and present you correct options accordingly.
<h3><strong>My objectives for next week:</strong></h3>
<ul>
	<li><strong>Implement the settings frame.</strong> It will contain optional parameters, llike the type of face or the output location.</li>
	<li><strong>Implement the about frame.</strong> This one will give information about the license and version, . .. of the software.</li>
	<li><strong>Work on packaging.</strong> When the two first objectives will be done, I plan on spending some time on the setup.py file. I have to add dependencies to wxpython to it.</li>
</ul>
<h3><strong>On a longer term:</strong></h3>
<ul>
	<li>Have a nice looking interface.</li>
	<li>Package the application for Windows and Linux (Ubuntu for now). I want the simplest possible installation for users.</li>
	<li>Update the documentation and web page</li>
	<li>Allow the user to create/save/load projects.</li>
</ul>
<strong>To get the last version of the Ivolution,<a title="ivolution last" href="https://github.com/jlengrand/FaceMovie/tree/gui_v2" target="_blank"> clone the gui_v2 branch on github.</a></strong>
