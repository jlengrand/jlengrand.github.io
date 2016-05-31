---
layout: post
status: publish
published: true
title: FFMPEG Make fails to compile
author: Julien Lengrand-Lambert
author_login: jlengrand
author_email: julien@lengrand.fr
author_url: http://www.lengrand.fr
categories:
- tips
tags:
- ffmpeg
- windows
- make
- compilation
comments: []
---

Hey there, 

Today, I downloaded the latest version of ffmpeg and trid to compile it from scratch.
Pretty soon, the console threw this error :

    Creating config.mak and config.h...
    /d/new-ffmpeg/mybuild/ffmpeg/library.mak:95: * missing separator. Stop.

It is worth noticing that I was compiling on Windows 7, using MinGW. Far from being my usual weapon for choice for compiling stuff.

As expected, this was a windows related issue, and was not directly coming from ffmpeg.
Windows and Linux have different ways to handle end of lines. Both may be right, both may be wrong.
But this is something that has to be taken care of.

So, I changed git end of line settings :

    $ git config --global core.autocrlf false

and checked out the repository from scratch again.

And guess what : Everything worked perfectly!

It is worth noticing that the second download was way slower for me though.
This is probably coming from Git having to reformat the code properly for every commit.

Cheers
