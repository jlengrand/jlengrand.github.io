---
layout: post
status: publish
published: true
title: Find whether a Windows dll is compiled for 32 or 64 bits on Linux
author: Julien Lengrand-Lambert
author_login: jlengrand
author_email: julien@lengrand.fr
author_url: http://www.lengrand.fr
wordpress_id: 896
wordpress_url: http://www.lengrand.fr/?p=896
date: 2013-10-26 16:33:36.000000000 +02:00
categories:
- misc
- tips
- programming
tags:
- windows
- linux
- objdump
- dll
- dependency walker
comments: []
---
This morning, I stumbled upon an unexpected problem; and found myself not knowing what to do.

I had to compile the native part of a library on Linux, based on the existing Windows dlls.
<strong>Before compiling, I needed to know if the Windows dlls were compiled for 32 or 64 bits.</strong>

It is quite easy to do on Windows, with tools such as <a title="dependency walker page" href="http://www.dependencywalker.com/" target="_blank">dependency walker</a>, but on Linux!?

I knew that for native linux (.so) files, <strong>objdump</strong> would be my weapon of choice.

So I gave it a shot, and tried:

{% highlight bash %}
$ objdump -x my_windows.dll | head -n 15 # returns the first 15 lines of the result

{% endhighlight %}

And here was the result :

{% highlight bash %}

libxuggle-5.dll: file format pei-i386

libxuggle-5.dll

architecture: i386, flags 0x00000133:

HAS_RELOC, EXEC_P, HAS_SYMS, HAS_LOCALS, D_PAGED

start address 0x6e741058

Characteristics 0x2306

executable

line numbers stripped

32 bit words

debugging information removed

DLL

{% endhighlight %}

Pretty neat, huh?

I was really not expecting objdump to be so efficient even on Windows stuff.

<strong>Well done, Linux. Well done.</strong>
