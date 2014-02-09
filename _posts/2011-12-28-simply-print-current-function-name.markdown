---
layout: post
status: publish
published: true
title: ! 'Simply print current function name '
author: Julien Lengrand-Lambert
author_login: jlengrand
author_email: julien@lengrand.fr
author_url: http://www.lengrand.fr
wordpress_id: 476
wordpress_url: http://www.lengrand.fr/?p=476
date: 2011-12-28 16:55:21.000000000 +01:00
categories:
- Python
tags:
- function name
- print
- debug
comments: []
---
Hi all,

When developing, I hate having to search in which portion of my code I am. For Tippy, I searched for a way to always display the function name in case of an error.

Hopefully, Python offers a simple (but curious) way to perform this.

Here is how to <strong>print your function name as a string</strong> in Python :

[python]
import sys

def tutut():
    &quot;&quot;&quot;
    Dum function displaying its name!
    &quot;&quot;&quot;
    print sys._getframe().f_code.co_name

if __name__ == '__main__':
    tutut()
[/python]

And here is the result

[bash]
[airballman@ubuntu:~]$ python tutut.py
tutut
[/bash]

There it is !

You can also find this tip in my Programming Tips page, in the <strong><a href="http://www.lengrand.fr/programming-tips-2/#python">Python section</a>.</strong>
