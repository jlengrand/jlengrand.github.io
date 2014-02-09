---
layout: post
status: publish
published: true
title: A simple way to watermark a batch of images
author: Julien Lengrand-Lambert
author_login: jlengrand
author_email: julien@lengrand.fr
author_url: http://www.lengrand.fr
wordpress_id: 422
wordpress_url: http://www.lengrand.fr/?p=422
date: 2011-12-20 17:35:10.000000000 +01:00
categories:
- programming
tags:
- photo
- bash
- watermark
- batch
- image magick
- github
comments: []
---
Hi all,

Some time ago, I was searching for a way to simply watermark images to put them on my <strong><a title="my flickr" href="http://www.flickr.com/photos/49365498@N03/">gallery</a></strong>.

I knew <strong><a title="digikam" href="http://www.digikam.org/">digikam</a></strong> could do this, but the package in debian was an old version and the feature was not inserted yet. In addition, I have never found a photo management software that would fit my needs yet . . .

I finally developed my own function with some bash and<strong> <a title="image magick" href="http://www.imagemagick.org/script/index.php">image magick</a>. </strong>I created it to be as simple to use as possible. It needs:
<ul>
	<li>an input folder</li>
	<li>an output folder</li>
	<li>a watermark image</li>
</ul>
When run, the script inserts the watermark in all images of the input folder and save them in the output folder.

[bash]
$ waterMark in_folder out_folder watermark_image
[/bash]

As a bonus, the script automatically detects whether an image is in landscape or portrait mode before inserting the watermark, so that it is always in the right side.

Here is an example of the result :

[caption id="attachment_424" align="aligncenter" width="200" caption="picture of the "jardin des plantes" in Nantes"]<a href="http://www.lengrand.fr/wp-content/uploads/2011/12/pourquoi_le_bitume__by_jlengrand-d4dp4ha.jpg"><img class="size-medium wp-image-424" title="Pourquoi le bitume?" src="http://www.lengrand.fr/wp-content/uploads/2011/12/pourquoi_le_bitume__by_jlengrand-d4dp4ha-200x300.jpg" alt="picture of the "jardin des plantes" in Nantes" width="200" height="300" /></a>[/caption]

This script is in an early stage for now, and should be upgraded with time. You can check out the <strong><a title="TODO list" href="https://github.com/jlengrand/batchWaterMarking">TODO list here. </a></strong>

You can download the script <strong><a title="my github" href="https://github.com/jlengrand/batchWaterMarking">on my gitHub</a>, </strong>or more simply download the project using git

[bash]

$ git clone git://github.com/jlengrand/batchWaterMarking.git

[/bash]

Feel free to fork the project or let me know about what would be useful for you.

Hope this will help some of you !

See ya ;)
