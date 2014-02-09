---
layout: post
status: publish
published: true
title: Multiprocessing using Python
author: Julien Lengrand-Lambert
author_login: jlengrand
author_email: julien@lengrand.fr
author_url: http://www.lengrand.fr
wordpress_id: 480
wordpress_url: http://www.lengrand.fr/?p=480
date: 2011-12-29 14:07:46.000000000 +01:00
categories:
- Python
tags:
- multiprocessing
- thread
- process
- speed
- sonar
- UUV
comments:
- id: 225
  author: Chris
  author_email: Cwilkes@ladro.com
  author_url: ''
  date: !binary |-
    MjAxMi0wMi0wOCAxNTo1NjowNCArMDEwMA==
  date_gmt: !binary |-
    MjAxMi0wMi0wOCAxNDo1NjowNCArMDEwMA==
  content: ! "Look at the Pool class, it will by default create a queue of all your
    submitted jobs and run up to your number of cores at the same time. \r\nHaving
    come from java I was really impressed with how easy it was to start working with
    Process."
- id: 226
  author: Julien Lengrand-Lambert
  author_email: julien@lengrand.fr
  author_url: http://www.lengrand.fr
  date: !binary |-
    MjAxMi0wMi0wOCAxNjowOTozNiArMDEwMA==
  date_gmt: !binary |-
    MjAxMi0wMi0wOCAxNTowOTozNiArMDEwMA==
  content: ! "Hi Chris, \r\n\r\nYou are right indeed. I coded this on my first time
    playing with Processes. For more elaborate code, Pools would be the best solution,
    but require some more work (and comprehension) from the user. \r\n\r\nBut I have
    an idea of where I could use these Pools and post some samples here soon :)."
- id: 269
  author: Twiggy
  author_email: rabikm@rediffmail.com
  author_url: http://www.yahoo.com/
  date: !binary |-
    MjAxMi0wMi0xNCAxOToyNToxNCArMDEwMA==
  date_gmt: !binary |-
    MjAxMi0wMi0xNCAxODoyNToxNCArMDEwMA==
  content: This is the peerfct post for me to find at this time
- id: 282
  author: Julien Lengrand-Lambert
  author_email: julien@lengrand.fr
  author_url: http://www.lengrand.fr
  date: !binary |-
    MjAxMi0wMi0xNSAwOTo0OToyMiArMDEwMA==
  date_gmt: !binary |-
    MjAxMi0wMi0xNSAwODo0OToyMiArMDEwMA==
  content: Well, Glad it helped ;)
---
Some time ago, I worked with real time processing of sonar images. My job was to detect mines on both sides of an <strong><a title="UUV" href="http://www.globalsecurity.org/intell/systems/uuv.htm">UUV</a></strong> equipped with <strong><a title="side scan sonar" href="http://en.wikipedia.org/wiki/Side-scan_sonar">Side-Scan sonars</a></strong>.

My algorithm had to run as fast as possible and I naturally ended up thinking about parallel processing. My application was kind of designed to be paralleled as at each instant I had two images coming (left and right side of my vehicle).

Most of computes now have at least 2 processors. Multiprocessing was then the best way to simply minimize computation time! In addition, as no data had to be passed from one application to the other (left and right images are totally unrelated) threads were obviously not the most interesting solution for me.

Basically, the following example will be perfect for applications in which<strong> the exact same task has to be performed several times on unrelated data :</strong>

Here is a simple multiprocessing example, coming from the <a title="python doc" href="http://www.python.org/doc/">Python documentation</a>:

[python]

from multiprocessing import Process

def f(name):
    print 'hello', name

if __name__ == '__main__':
    p = Process(target=f, args=('bob',))
    p.start()
    p.join()

[/python]

This example creates a <strong>process</strong>, performing the <strong>f</strong> function. The first line indicates the function to be run and its arguments. The second line (<strong>start) </strong>starts the processus.

Finally, the <strong>join</strong> keyword waits for the function to finish properly and exits.

Creating two processes now appears to be pretty simple :

[python]

from multiprocessing import Process

def f(name):
    print 'hello', name

if __name__ == '__main__':
    p1 = Process(target=f, args=('la meute',))
    p2 = Process(target=f, args=('tout le monde',))
    p1.start()
    p2.start()
    p1.join()
    p2.join()

    print('Exiting!)

[/python]

In  this second example, the <strong>print </strong>will be performed only when <strong>p1</strong> and <strong>p2</strong> have been killed.

In order to enhance you productivity, a simple idea is to create as much processes as the <strong>number of cores in your computer</strong>. Once again, Python has already made the work for you.

[python]

nb_processes = multiprocessing.cpu_count()

[/python]

Here it is, Your application should now run slightly faster !

In case you <strong>don't know the difference between process and thread</strong>,<a title="diff process thread" href="http://stackoverflow.com/questions/200469/what-is-the-difference-between-a-process-and-a-thread"> you should have a look here</a> .
