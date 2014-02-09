---
layout: post
status: publish
published: true
title: Get the power of Matlab in command line
author: Julien Lengrand-Lambert
author_login: jlengrand
author_email: julien@lengrand.fr
author_url: http://www.lengrand.fr
wordpress_id: 252
wordpress_url: http://www.lengrandlambert.fr/wordpress/?p=252
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

I got a small hint for you if you use <strong><a title="matlab" href="http://www.mathworks.fr/" target="_blank">Matlab</a></strong> on a daily basis but still love your command line!
<h3></h3>
<div id="post-body-872517502060080737">

I am really not a <a title="IDE" href="http://en.wikipedia.org/wiki/Integrated_development_environment" target="_blank">IDE</a> kinda guy and always try to avoid using a huge interface when an editor is enough. Personally,  I haven't found a more powerful tool than the <strong>emacs/terminal</strong> combination yet.

In addition, the Matlab interface is fully coded in Java and is way too much ram-consuming imho. So I decided to get rid of it! Simply run

[matlab]
$ matlab -nojvm -r script //run without implying the jvm
[/matlab]

or

[matlab]
$ matlab -nodisplay -nosplash -nodesktop -r script
[/matlab]

The result is a Matlab command line interface. You will simply have to use your favourite editor to create your scripts, and then run them using the command line.

The plots and figures will be displayed without any problem.

There is a small drawback however for <strong>Windows users</strong> : The <strong>autocompletion</strong> won't be available as it is a <strong>Java feature</strong> under Windows.

No problem under <strong>Linux</strong> (once again :p)!

Here is a screenshot of the result, so that you get the idea :

<a title="Matlab in command line" href="http://www.lengrand.fr/wp-content/uploads/2011/11/matlab_cl.png"><img class="size-large wp-image-263 alignnone" title="matlab in command line" src="http://www.lengrand.fr/wp-content/uploads/2011/11/matlab_cl.png" alt="" /></a>

</div>
