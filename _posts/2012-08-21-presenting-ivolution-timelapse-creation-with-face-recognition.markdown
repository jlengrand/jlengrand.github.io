---
layout: post
status: publish
published: true
title: ! 'Ivolution: Your personal timelapse'
author: Julien Lengrand-Lambert
author_login: jlengrand
author_email: julien@lengrand.fr
author_url: http://www.lengrand.fr
wordpress_id: 689
wordpress_url: http://www.lengrand.fr/?p=689
date: 2012-08-21 13:33:59.000000000 +02:00
categories:
- OpenCV
- Computer Vision
- Python
- Ivolution
tags:
- image processing
- git
- ivolution
- face recognition
- timelapse
- video
- everyday
- time lapse
comments: []
---
Here comes a new blog post, after almost two months of silence.

I was in holidays for the last two weeks, and decided not to touch the computer for all that time. And I must admit that with the combination of my friends coming from France and the perfect weather here, it was no that difficult. In fact, I even switched my phone off for a week (well ok, I had forgotten my pin code ^^).
<div></div>
But lately, I spent most of my free time working on <strong><a title="Ivolution" href="http://jlengrand.github.com/FaceMovie/" target="_blank">Ivolution</a></strong>, and this is what I want to present you today !

Basically, it is an application that aims at helping you create videos of yourself over time. <strong>Simply take a picture of your face every now and then for some time, and Ivolution will generate a timelapse with it. </strong>I use <strong>face recognition</strong> so that your face overlaps on all pictures.
<div></div>
But as Napoleon once said :
<blockquote>Un petit dessin vaut mieux qu'un long discours</blockquote>
here is a demonstration of Ivolution capabilities.

http://www.youtube.com/watch?v=9ZpKnSjvmXo

I have been working on it for dozens of hours now, and slowly see it taking shape. If I had a functional core for some weeks now, it is far from enough to get a nice product and much is still missing (nice interface, performance, documentation, easy installation, . . . ). And <a title="Job Space" href="http://www.lengrand.fr/job-space/" target="_blank">as a computer vision engineer</a>, it takes me a lot of time to implement all those elements !
<div></div>
But some time ago my very first early user,<a title="G+ Ignacio" href="https://plus.google.com/100142585105145842914/posts" target="_blank"> Ignacio Martinez</a> (Kudos to him!) lately informed me about the <a title="Ubuntu App Showdown" href="http://developer.ubuntu.com/showdown/" target="_blank">Ubuntu App Showdown</a> and I decided to give it a shot. I had three weeks to transform my bunch of classes into a proper product . In fact, I lost countless hours trying to package my projects into a proper deb file, and could not make it to the deadline.
<div></div>
Hopefully, all this work is not lost! The perspective of a contest gave me a big motivation push,  and <strong>I now have a first beta version for Ubuntu users</strong> including a User Interface! Here is what it looks like (yes, I would benefit from more designer skills) :
<div></div>
<div></div>
<div>

[caption id="" align="aligncenter" width="294"]<a href="https://dl.dropbox.com/u/4286043/ivolution_gtk.png"><img title="Ivolution interface" src="https://dl.dropbox.com/u/4286043/ivolution_gtk.png" alt="" width="294" height="547" /></a> Ivolution interface[/caption]

</div>
<div></div>
<strong><a title="ivolution git" href="http://jlengrand.github.com/FaceMovie/" target="_blank">You can find it here</a></strong>, and you need only one minute to install it (just follow the <a title="README Ivolution" href="https://github.com/jlengrand/FaceMovie/blob/master/README.markdown" target="_blank">README</a>, and everything should be fine).As I said, there is still a lot to be done to transform it into a nice application, but I think the project has <strong>met his first milestone</strong>.
<div></div>
Just getting out of holidays, my batteries are full up and I have a lot of ideas to implement.Here are some of my next objectives for the coming weeks :
<ul>
	<li>Redesign the GUI so that the application <strong>can be used by Windows and Mac users</strong>.</li>
	<li><strong>Create proper installers</strong>, to ease installation.</li>
	<li><strong>Implement a save/load project capability</strong>. For now, users always have to start from scratch. I want to change that</li>
	<li><strong>Increase performance</strong>. Face recognition is complex, and the processing can be long depending on the size of the images.</li>
</ul>
<div></div>
If you like the idea, <strong>give it a shot and let me know if you like it</strong> ! <a title="issues ivolution" href="https://github.com/jlengrand/FaceMovie/issues?state=open" target="_blank">Feel free to post bugs here</a>, any comment is appreciated.

Starting now, I'll write a <strong>weekly update</strong> about the status of the project to keep you informed.Hope some of you will like it ! And if you want to support the project, feel free to <a title="flattr" href="https://flattr.com/thing/712398" target="_blank">Flattr</a> or <a title="gittip me" href="https://www.gittip.com/jlengrand/" target="_blank">Gittip</a> me ;)
<div>

<strong>P.S:</strong> A last thing about the project name. You might see both <strong>Ivolution</strong> and <strong>Facemovie</strong> as a name for the project. The difference is subtle, and is going to disappear in the future. Facemovie refers to the core application, while Ivolution is the whole project, that uses Facemovie's API.

</div>
<div></div>
