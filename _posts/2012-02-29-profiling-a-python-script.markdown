---
layout: post
status: publish
published: true
title: Profiling a Python Script
author: Julien Lengrand-Lambert
author_login: jlengrand
author_email: julien@lengrand.fr
author_url: https://www.lengrand.fr
wordpress_id: 546
wordpress_url: https://www.lengrand.fr/?p=546
date: 2012-02-29 11:43:08.000000000 +01:00
categories:
- Python
tags:
- project euler
- profile
- profiler
- module
- stack overflow
comments: []
---
Here are some simple ways to profile Python scripts.I heavily use this to check my <strong><a title="PE solutions" href="https://github.com/jlengrand/project_euler" target="_blank">Project Euler solutions</a></strong>.
<h1></h1>
<h1><strong>SOLUTION 1:</strong></h1>
The main common option would be to use the <a title="profile" href="https://docs.python.org/library/profile.html?highlight=profile#cProfile" target="_blank"><strong>profile</strong> </a>(or <strong><a title="cprofile" href="https://docs.python.org/library/profile.html?highlight=profile#cProfile" target="_blank">cprofile</a></strong>) module.There are two different ways of using it :
<ul>
	<li>As a module, by directly running</li>
</ul>
<div>{% highlight python %}
python -m cProfile script.py
{% endhighlight %}

</div>
<div></div>
<div>
<ul>
	<li>In your code, by importing the utilities</li>
</ul>
<div>{% highlight python %}
import cProfile
cProfile.run('function()') # in your __main__
{% endhighlight %}

<em>Bonus : You can use several options for sorting results using the -s switch (cumulative/name/time/file sorting are available).</em>
<h1><strong>SOLUTION 2:</strong></h1>
If you want to avoid using a command line, or you don't have the profile module installed; here os another possibility. There is also the <strong><a title="timeit module" href="https://docs.python.org/library/timeit.html" target="_blank">timeit </a></strong>module available.

{% highlight python %}
import timeit
t1 = timeit.Timer("function()", "from __main__ import function")
print t1.timeit(1)
{% endhighlight %}

I use this option on Eclipse because I didn't want to install the profile module on Windows.

This is however less clear, and way less detailed while still useful :).

Choose you profiler option and get on <a title="PE" href="https://projecteuler.net/" target="_blank"><strong>Project Euler</strong> </a>!

[<a title="SO" href="https://stackoverflow.com/questions/582336/how-can-you-profile-a-python-script" target="_blank">Stack Overflow</a>]

</div>
</div>
