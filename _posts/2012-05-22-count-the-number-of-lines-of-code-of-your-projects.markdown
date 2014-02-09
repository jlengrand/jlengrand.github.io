---
layout: post
status: publish
published: true
title: Count the number of lines of code of your projects
author: Julien Lengrand-Lambert
author_login: jlengrand
author_email: julien@lengrand.fr
author_url: http://www.lengrand.fr
wordpress_id: 605
wordpress_url: http://www.lengrand.fr/?p=605
date: 2012-05-22 12:40:04.000000000 +02:00
categories:
- tips
tags:
- bash
- software
- development
- command
- lines
comments: []
---
After having finished a project, I always like to know its actual size. It does not give any value to my work, but it is always fun to see :)

I found this simple command that will pop out the number of lines of code for a given file extension.

{% highlight bash %}

cat `find . -name "*.py"` | wc -l

{% endhighlight %}

You can also do it for a whole folder

{% highlight bash %}

find . -name "*.py" | xargs wc -l

{% endhighlight %}
