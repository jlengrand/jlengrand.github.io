---
layout: post
status: publish
published: true
title: Synchronize config files between computers
author: Julien Lengrand-Lambert
author_login: jlengrand
author_email: julien@lengrand.fr
author_url: http://www.lengrand.fr
wordpress_id: 33
wordpress_url: http://www.lengrandlambert.fr/wordpress/?p=33
date: 2011-10-18 13:17:55.000000000 +02:00
categories:
- tips
tags:
- windows
- dropbox
- synchronize
- backup
- config
comments: []
---
Hi all,

Today, a small hint for Linux users having <strong>DropBox</strong> running on their computer. I guess everyone knows what DropBox is. . .

If not, feel free to have a look <a href="http://www.dropbox.com/referrals/NTQyODYwNDM5?src=global9">there</a> (and win 250 more mos for me and you at the same time). In one word, DB allows to have a folder of your computer on the cloud. This way, you have access to you important files, wherever you are.

Most of us now have multiple computers (at work, at home, laptop, . . . ). All of them are configured, and often have similar configurations. And you know how important those files are  in order to feel weel and have his feets on a Linux distribution.

I am used to tune my configuration files, such as my .bashrc and so. And it is quite painful to find an alias one day and have to search for it the day after on another computer.

DropBox offers a simple solution to this problem, as with <strong>symbolic links</strong> we can keep trace of our different configuration files live.

Here is the way to do it:

Create a new folder in your DropBox repo :

{% highlight bash %}
$ mkdir DropBoxRepo/laptopConfig
{% endhighlight %}

Move in it and create simlinks to each config file you want to backup (for example your .bashrc):

{% highlight bash %}
$cd DropBoxRepo/laptopConfig; ln -s ~/.bashrc .bashrc
{% endhighlight %}
Voilà!

Now, you have access to a copy of your bashrc <strong>wherever you go</strong>, and may use it to tune another computer. And it works even with entire folders (like your ~/bin)

In case all you computer have the exact same configuration files, you might do the other way around, and use your DropBox folder as basis for your config files :

{% highlight bash %}
$cd ~; ln -s  DropBoxRepo/Config/.bashrc .bashrc
{% endhighlight %}

Be careful however, because modifications will have to be done in the DropBox folder now. And updates will only take place after your DropBox synchronization. <strong>So avoid dangerous ideas</strong>, such as synchronizing your /etc/fstab :D

&nbsp;

That's all for today,

<strong>C U</strong>
