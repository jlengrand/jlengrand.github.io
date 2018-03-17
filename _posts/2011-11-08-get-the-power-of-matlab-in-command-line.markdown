---
layout: post
status: publish
published: true
title: Get the power of Matlab in command line
author: Julien Lengrand-Lambert
author_login: jlengrand
author_email: julien@lengrand.fr
author_url: https://www.lengrand.fr
wordpress_id: 252
wordpress_url: https://www.lengrandlambert.fr/wordpress/?p=252
date: 2011-11-08 15:14:34.000000000 +01:00
categories:
- Matlab
tags:
- windows
- matlab
- command line
- bash
comments: []
---
Hi all,

I got a small hint for you if you use <strong><a title="matlab" href="https://www.mathworks.fr/" target="_blank">Matlab</a></strong> on a daily basis but still love your command line!

<div id="post-body-872517502060080737">

I am really not a <a title="IDE" href="https://en.wikipedia.org/wiki/Integrated_development_environment" target="_blank">IDE</a> kinda guy and always try to avoid using a huge interface when an editor is enough. Personally,  I haven't found a more powerful tool than the <strong>emacs/terminal</strong> combination yet.

In addition, the Matlab interface is fully coded in Java and is way too much ram-consuming imho. So I decided to get rid of it! Simply run

{% highlight matlab %}

$ matlab -nojvm -r script //run without implying the jvm

{% endhighlight %}

or

{% highlight matlab %}

$ matlab -nodisplay -nosplash -nodesktop -r script

{% endhighlight %}


The result is a Matlab command line interface. You will simply have to use your favourite editor to create your scripts, and then run them using the command line.

The plots and figures will be displayed without any problem.

There is a small drawback however for <strong>Windows users</strong> : The <strong>autocompletion</strong> won't be available as it is a <strong>Java feature</strong> under Windows.

No problem under <strong>Linux</strong> (once again :p)!

Here is a screenshot of the result, so that you get the idea :

<center><a title="Matlab in command line" href="{{ site.url }}/images/posts/2011/11/matlab_cl.png"><img class="size-large wp-image-263 alignnone" title="matlab in command line" src="{{ site.url }}/images/posts/2011/11/matlab_cl.png" alt="" /></a></center>

</div>
