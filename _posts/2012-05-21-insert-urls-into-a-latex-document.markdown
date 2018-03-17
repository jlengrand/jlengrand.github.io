---
layout: post
status: publish
published: true
title: Insert urls into a Latex document
author: Julien Lengrand-Lambert
author_login: jlengrand
author_email: julien@lengrand.fr
author_url: https://www.lengrand.fr
wordpress_id: 598
wordpress_url: https://www.lengrand.fr/?p=598
date: 2012-05-21 13:18:59.000000000 +02:00
categories:
- tips
tags:
- latex
- url
- document
- texmaker
comments: []
---
A really simple tip today, that helped me a lot some time ago.

If you use <a title="latex" href="https://fr.wikipedia.org/wiki/LaTeX" target="_blank">LaTeX</a> to create your reports, you may want to include weblinks or urls.

The process is quite simple, simply include the url package in the header of your document

{% highlight bash %}

\usepackage{url}

{% endhighlight %}

and then insert your desired url :

{% highlight bash %}

\url{https://www.lengrand.fr}

{% endhighlight %}

You may want to play a bit, a there are different url styles. Here is a simple example

{% highlight bash %}

\urlstyle{rm}

{% endhighlight %}

Of course, all those links are still active after your pdf conversion!

Long time I haven't used Latex, I tend to write everything with <a title="GDocs" href="https://docs.google.com/a/spacemetric.com/#home" target="_blank">GDocs </a>now :)
