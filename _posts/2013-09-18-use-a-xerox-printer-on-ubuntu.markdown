---
layout: post
status: publish
published: true
title: Use a Xerox printer on Ubuntu
author: Julien Lengrand-Lambert
author_login: jlengrand
author_email: julien@lengrand.fr
author_url: http://www.lengrand.fr
wordpress_id: 882
wordpress_url: http://www.lengrand.fr/?p=882
date: 2013-09-18 09:11:56.000000000 +02:00
categories:
- tips
tags:
- ubuntu
- linux
- xerox
- '13.04'
- printer
- phaser
- aptitude
comments: []
---
A quick and small post that could save some of you a few hours.

If you're like me, you may have a <strong><a title="Xerox website" href="http://www.office.xerox.com/">Xerox</a> printer</strong> of phazer in your work or home environmenent.

And your <strong>ubuntu</strong> is unable to print any document on this printer, displaying fancy errors like <a title="filter failed forum" href="http://ubuntuforums.org/showthread.php?t=2136163" target="_blank"><strong>"filter failed"</strong></a>.

Before going on the <a title="xerox support" href="http://www.support.xerox.com/support/enus.html" target="_blank">Xerox website</a> searching for ugly tar.gz files to install; and read dozens of forums and documentation pages to finally get the printer to work;
try to install <a title="foomatic website" href="http://www.linuxfoundation.org/collaborate/workgroups/openprinting/databasefoomatic" target="_blank"><strong>foomatic-db</strong></a>.

It is as simple as

[bash]
sudo apt-get install foomatic-db

[/bash]


on an ubuntu (13.04, in my case).

This worked like a charm for me.
The part is don't get is why this foomatic-db is so hard to find. I had to search for the package listing, making searches about xerox drivers to find it.
I found no reference about it on the internet what so ever with the "filter failed" keywords.

Hope this helps some of you.

Cheers
