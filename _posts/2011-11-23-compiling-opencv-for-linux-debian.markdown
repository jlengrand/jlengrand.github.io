---
layout: post
status: publish
published: true
title: Compiling OpenCV for Linux (Debian)
author: Julien Lengrand-Lambert
author_login: jlengrand
author_email: julien@lengrand.fr
author_url: http://www.lengrand.fr
wordpress_id: 293
wordpress_url: http://wordpress.lengrandlambert.fr/?p=293
date: 2011-11-23 14:00:39.000000000 +01:00
categories:
- OpenCV
tags:
- image processing
- ubuntu
- debian
- compiling
comments: []
---
I am sure that most of you know <strong><a title="OpenCV" href="http://en.wikipedia.org/wiki/OpenCV" target="_blank">OpenCV</a></strong>, the open-source Computer Vision library initially developed by Intel.

Synaptic, the packages manager of all Debian based distributions  do contain opencv packages (namely libcv, libcvaux and libhighgui). But they are seriously outdated (2.1 in Ubuntu 11.10 when the last stable release <a title="opencv_sourceforge" href="http://sourceforge.net/projects/opencvlibrary/" target="_blank">on sourceforge </a>is the 2.3.1a).

If you want to use some new features (such as the new Python bindings in my case), you will have to compile OpenCV by yourself.

An excellent <strong>install guide for Debian</strong> is available on <a title="opencv_wiki" href="http://opencv.willowgarage.com/wiki/InstallGuide%20%3A%20Debian" target="_blank">the OpenCV Wiki</a>. Do not forget to install libgtk2.0 too if you want to use screen display functions later.
<div>[bash]
[jlengrand@ubuntu:~/downloads/OpenCV-2.3.1/release]$sudo apt-get install libgtk2.0-0 libgtk2.0-dev
[/bash]

</div>
But during the compilation, you might encounter the following <strong>error</strong> :

[bash]

...

/home/jlengrand/downloads/OpenCV-2.3.1/modules/highgui/src/cap_libv4l.cpp:1673: error: ‘struct CvCaptureCAM_V4L’ has no member named ‘memoryBuffer’
make[2]: *** [modules/highgui/CMakeFiles/opencv_highgui.dir/src/cap_libv4l.o] Error 1
make[1]: *** [modules/highgui/CMakeFiles/opencv_highgui.dir/all] Error 2
[/bash]

This error is due to libv4l, which causes problems to openCV. Here is a simple way to get rid of the error :
<ul>
	<li><strong>Remove libv4l</strong> for your system.</li>
</ul>
<div><strong>WARNING</strong> : <em>Do not reboot before the end of the operations, or your display will fail to start!</em></div>
<div>[bash]
[jlengrand@ubuntu:~/downloads/OpenCV-2.3.1/release]$ sudo apt-get remove libv4l-dev libv4l-0
The following packages will be REMOVED:
gstreamer0.10-plugins-good libgstfarsight0.10-0 libpurple-bin libpurple0 libv4l-0 libv4l-dev pidgin vlc vlc-nox vlc-plugin-notify vlc-plugin-pulse
0 upgraded, 0 newly installed, 11 to remove and 37 not upgraded.
After this operation, 28.1 MB disk space will be freed.Do you want to continue [Y/n]? Y
[/bash]

</div>
<div>Keep trace of all packages noted for removal, to reinstall them in last step.</div>
<div>
<ul>
	<li>Then <strong>finish OpenCV compilation</strong>:</li>
</ul>
<div>
<div>[bash]
[jlengrand@ubuntu:~/downloads/OpenCV-2.3.1/release]$ make
...
[jlengrand@ubuntu:~/downloads/OpenCV-2.3.1/release]$ sudo make install
[/bash]

</div>
</div>
<div>It should compile without error.</div>
<div>
<ul>
	<li>Finally, you simply have to<strong> reinstall all previously removed packages</strong> (which depends on your system).</li>
</ul>
<div>
<div>[bash]
[jlengrand@ubuntu:~/downloads/OpenCV-2.3.1/release]$sudo apt-get install gstreamer0.10-plugins-good libgstfarsight0.10-0 libpurple-bin libpurple0 libv4l-0 libv4l-dev pidgin vlc vlc-nox vlc-plugin-notify vlc-plugin-pulse
[/bash]

</div>
</div>
</div>
</div>
<div>There it is, the library is successfully <strong>installed</strong>, you may use it as you wish ;).</div><!--:-->
