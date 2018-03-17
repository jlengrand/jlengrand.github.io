---
layout: post
status: publish
published: true
title: Easily change file separator
author: Julien Lengrand-Lambert
author_login: jlengrand
author_email: julien@lengrand.fr
author_url: http://www.lengrand.fr
wordpress_id: 592
wordpress_url: http://www.lengrand.fr/?p=592
date: 2012-05-17 15:37:56.000000000 +02:00
categories:
- tips
- programming
tags:
- bash
- sed
- separator
- file
- csv
- awk
comments: []
---
You may already have found yourself in front of a huge csv file to be processed. Five minutes after having started working, you realize that you want spaces instead of commas in your file. Only problem, the file is 500 megabytes big.

Do you run Linux ? In this case, your case will be solved in 10 seconds (who said as usual ? :p).

Simply open a console and run this line

{% highlight bash %}

sed -e $"s/,/\ /g" myfile > newfile

{% endhighlight %}

or more generally,

{% highlight bash %}

sed -e $"s/old_separator/new_separator/g" myfile > newfile

{% endhighlight %}

If not, well <a title="why linux is better" href="http://www.whylinuxisbetter.net/" target="_blank">you may want to think about switching</a> then :)

Thanks to <a title="frafra" href="http://liveusb.info/dotclear/" target="_blank">Frafra</a> for the tip ;)
