---
layout: post
status: publish
published: true
title: Execute a function given its name as a string!
author: Julien Lengrand-Lambert
author_login: jlengrand
author_email: julien@lengrand.fr
author_url: http://www.lengrand.fr
wordpress_id: 526
wordpress_url: http://www.lengrand.fr/?p=526
date: 2012-02-16 22:30:25.000000000 +01:00
categories:
- programming
- Lua
tags:
- web
- html
- software
- lua
- string
- function
comments: []
---
Well, interesting problem. . . if you are not working with Lua.
Some time ago, I developed a web interface that would interface with <a title="mipsee" href="http://www.advansee.com/mipsee.html">the camera I was working with</a>.
Being a fully autonomous system, <strong>Mipsee</strong> has limited ressources and<strong> PHP and databases</strong> were surely not the good solution for an embedded interface. I finally ended up with a<strong> Lua + HTML combo</strong>.
The idea was to be able to start a computer vision application (face detection, blob tracking, . . .) and see the results in real time directly from the web interface.
I searched for a simple way to detect and integrate new applications as they would be developed, <strong>without modifying the interface layer</strong>. In addition, those application would have <strong>variable inputs and outputs</strong>.
My solution was to bind any new binary with an interface file that would define inputs and outputs for the given application.

And here came the issue : I would have <strong>the name of the binary as a string value</strong>. <strong>How to launch it</strong> when needed?
Well, this could be a problem in C; but I was in Lua . . . Magic trick !
Problem solved in 3 simple lines of code :

{% highlight php %}

post_func = loadstring("param = printf(\"Hello ! \")")
post_func()
appli_repo = os.execute(param)

{% endhighlight %}

if I want to execute param.

At first glance, I hated working with <a title="lua" href="http://www.lua.org/"><strong>Lua</strong> </a>which was way<strong> too messy and undocumented</strong> for me. But I'm still impressed by the capabilities of the language when correctly used.
For those who don't know Lua, this is a (portguese) language particularly used in video games. The user interface of WOW is for example fully developed in Lua  (and I still wonder why . . .).

So, if some of you know any other advantage of working with Lua, let me know ;).
