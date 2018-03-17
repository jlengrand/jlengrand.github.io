---
layout: post
status: publish
published: true
title: ! 'XBMC: Share your external drive to your other computers'
author: Julien Lengrand-Lambert
author_login: jlengrand
author_email: julien@lengrand.fr
author_url: http://www.lengrand.fr
wordpress_id: 842
wordpress_url: http://www.lengrand.fr/?p=842
date: 2013-02-27 10:56:50.000000000 +01:00
categories:
- misc
tags:
- xbmc
- xbmcbuntu
- media server
- sharing
- network
- samba
comments: []
---
As already said <a title="XBMC won’t leave me ever again" href="http://www.lengrand.fr/2013/02/xbmc-wont-leave-me-ever-again/" target="_blank">in my last post</a>, I gave my first try to <a title="xbmc website" href="http://xbmc.org/" target="_blank"><strong>xbmc</strong> </a>last week. The basic setup was almost fully automatic.

There was one thing I had to do manually though, and I want to share it here because I didn't find the solution anywhere on XBMC forums.
My idea is simple : <strong>attached to my xbmc laptop</strong> is a 2To external hard drive that will contain all my movies, pictures, . . .
Those things used to be on my other computers, and I don't want to duplicate content so<strong> I wanted this drive to be accessible to all the other computers on my network.</strong>

The way to do it is quite simple in the end, if you know where to search :
By default, xbmc already shares its libraries on the network (Movies, Music, ...). All of this is defined in<strong><em> /etc/samba/smb.conf</em></strong>.

So the solution is to add another section to this file. That will share it on the network too.
By default, your external hard drives should be mounted in <strong><em>/media</em></strong>.

So if I want to share my external hard drive (called Elements) on the network, I'd do something like that:

{% highlight bash %}
[Elements]
path = /media/Elements
comment = data drive
writable = yes
browsable = yes
guest ok = yes

{% endhighlight %}

The <strong>guest ok </strong>option will allow anyone on your local network to access the drive without having to authenticate, so be careful.
Now check that the other users will be able to read/write on the device

{% highlight bash %}
$ ll /media/Elements

{% endhighlight %}

and if not, run

{% highlight bash %}

$ chmod -R 755 /media/Elements

{% endhighlight %}

and restart samba (or the whole computer if you have a doubt :))

{% highlight bash %}

$ /etc/init.d/sbmd restart

{% endhighlight %}

Now check on your other computers, you should be able to access your new folder without troubles :).

On my Win7, that simply means going to my file explorer and double clicking on the Xbmcbuntu icon that appears.

Hope this can help someone!
