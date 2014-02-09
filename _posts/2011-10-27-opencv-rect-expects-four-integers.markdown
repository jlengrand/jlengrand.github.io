---
layout: post
status: publish
published: true
title: ! 'OpenCV : ''rect'' expects four integers'
author: Julien Lengrand-Lambert
author_login: jlengrand
author_email: julien@lengrand.fr
author_url: http://www.lengrand.fr
wordpress_id: 207
wordpress_url: http://www.lengrandlambert.fr/wordpress/?p=207
date: 2011-10-27 09:48:25.000000000 +02:00
categories:
- programming
- OpenCV
- Computer Vision
- Python
tags:
- windows
- image processing
comments: []
---
You may encounter this error when using <a title="opencv" href="http://opencv.willowgarage.com/wiki/" target="_blank">OpenCV</a> with <strong>Python bindings, </strong>while trying to use the rectangle structure.

Here is an example :

{% highlight python %}
#!/usr/bin/env python

import cv

img = cv.LoadImage("test.jpg")
dims = cv.GetSize(img)
roi = [0, 0, dims[0] / 2, dims[1] / 2 ]
cv.SetImageROI(img, roi)
{% endhighlight %}

You will get this result:

{% highlight python %}
Traceback (most recent call last):
  File "newfile.py", line 8, in <module>
    cv.SetImageROI(img, roi)
TypeError: CvRect argument 'rect' expects four integers
{% endhighlight %}

The answer is pretty simple, you have to set rect as a <strong>tuple </strong>and not a list<strong>:</strong>

{% highlight python %}
roi = (0, 0, dims[0] / 2, dims[1] / 2 )
{% endhighlight %}

There it is, pretty simple, isn't?!

I still lost 15 minuts searching for it yesterday ^^, won't do it twice :D

A small <strong>warning</strong> however, the values of the tuple <strong>can't be changed</strong> once initialized !

See ya
