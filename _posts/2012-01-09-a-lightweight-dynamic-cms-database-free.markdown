---
layout: post
status: publish
published: true
title: A lightweight dynamic CMS, database free!
author: Julien Lengrand-Lambert
author_login: jlengrand
author_email: julien@lengrand.fr
author_url: http://www.lengrand.fr
wordpress_id: 494
wordpress_url: http://www.lengrand.fr/?p=494
date: 2012-01-09 13:42:28.000000000 +01:00
categories:
- misc
tags:
- pluxml
- website
- CMS
- database
- lightweight
- dynamic
- xml
- wordpress
comments:
- id: 144
  author: My minimalist dark Pluxml theme | loup2fu
  author_email: ''
  author_url: http://www.lengrand.fr/2012/01/my-minimalist-dark-pluxml-theme/
  date: !binary |-
    MjAxMi0wMS0xMCAxMzoyOToxOCArMDEwMA==
  date_gmt: !binary |-
    MjAxMi0wMS0xMCAxMjoyOToxOCArMDEwMA==
  content: ! '[...] Post navigation &larr; Previous [...]'
- id: 21593
  author: Thomas
  author_email: kriuks1@hotmail.com
  author_url: ''
  date: !binary |-
    MjAxMy0xMi0wOCAyMDo1NToxMCArMDEwMA==
  date_gmt: !binary |-
    MjAxMy0xMi0wOCAxOTo1NToxMCArMDEwMA==
  content: ! "Hello,\r\n\r\nThis platform is quite nice, but there are some questions
    that bother me. Is Pluxml good for websites with lots of traffic, say 1000 unique
    IP in a  day? MySQL is a database, it's designed for vast database IO requests,
    what about XML? Do you have any opinion about using pluxml for websites which
    have huge traffic or lots of content which is searched by lots of users daily?
    Thanks for the answer."
- id: 24348
  author: Julien Lengrand-Lambert
  author_email: julien@lengrand.fr
  author_url: http://www.lengrand.fr
  date: !binary |-
    MjAxNC0wMi0wNSAxNToyOTo0NiArMDEwMA==
  date_gmt: !binary |-
    MjAxNC0wMi0wNSAxNDoyOTo0NiArMDEwMA==
  content: ! "Hey, \r\n\r\nSorry for the late reply. Your comment ended in the spam
    box, for some strange reason . . .\r\n\r\nPluxml has been built mostly for small
    websites, to help deploy simply and rapidly without a database. So nothing is
    really made by pluxml itself to handle large loads.\r\nThat being said, I would
    say that the impact will mainly depend on your hardware. The bandwidth should
    probably be roughly the same as for  say Wordpress (and probably even smaller).
    But your server will have to fetch more xml files on your fileserver.\r\n\r\nSo
    I'd say that for a pluxml website with a large traffic, you should probably look
    at SSDs more than anything else, and add a caching layer."
---
Before choosing <strong><a title="wordpress" href="http://wordpress.org/" target="_blank">Wordpress</a></strong> as a <strong><a title="CMS wiki" href="http://en.wikipedia.org/wiki/Content_management_system" target="_blank">CMS</a></strong>, I searched for a minimalist way to both learn web development and get a nice looking blog.
My choice went To <strong><a title="pluxml" href="http://www.pluxml.org/" target="_blank">Pluxml</a></strong>, which is a french initiative to run websites <strong>without databases</strong>. This way, you can freely use it on a portable USB key. Everything is based on the XML format.

<strong>PluXml</strong> is a full CMS developed in php which contains lots of tools, from editors to admin menus or comments handling. It supports multiple users with different credentials.
I think this is a perfect choice for people that search for a<strong> lightweight solution</strong> and know a bit of programming languages.
In fact, I switched to <strong>Wordpress</strong> only because I wanted to have a multilingual blog, but still use PluXml for personal use.

The only drawback of <strong>Pluxml</strong> would be its <strong>french roots</strong>. Almost all the documentation, forums and support that can be found is in french and so are the comments of the php files ! But as its success grows, there should be more english language coming I think . . .

The installation is way simple :
<ul>
	<li><a title="pluxml latest" href="http://www.pluxml.org/" target="_blank">Simply download the last version of Pluxml here</a>, and unzip it in the desired folder of your server.</li>
</ul>
<div>

[caption id="attachment_495" align="aligncenter" width="584" caption="main install page of pluxml"]<a href="http://www.lengrand.fr/wp-content/uploads/2012/01/install.jpeg"><img class="size-large wp-image-495" title="install of pluxml" src="http://www.lengrand.fr/wp-content/uploads/2012/01/install-1024x616.jpg" alt="main install page of pluxml" width="584" height="351" /></a>[/caption]

</div>
<div></div>
<ul>
	<li>Connect to the main page of your website. You will be answered to set up the CMS.</li>
	<li>Simply click on install if all dependencies you need are installed. Note that you can choose the language you want to use. Immediately, you will be redirected to the main page of your website.</li>
	<li>Finally, <strong>remove the install.php</strong> file that can be found in the sources of pluxml to avoid any security breach.</li>
</ul>
<strong>Your website is now ready for use !</strong>
You can change most of the settings, write articles and handle comments in the admin menu :

[caption id="attachment_496" align="aligncenter" width="584" caption="some admin settings of Pluxml"]<a href="http://www.lengrand.fr/wp-content/uploads/2012/01/admin_settings.jpeg"><img class="size-large wp-image-496" title="admin settings of Pluxml" src="http://www.lengrand.fr/wp-content/uploads/2012/01/admin_settings-1024x618.jpg" alt="some admin settings of Pluxml" width="584" height="352" /></a>[/caption]

The system to add <strong>plugins</strong> is similar to most of CMS, <a title="plugins page pluxml" href="http://www.pluxml.org/?static7/download  " target="_blank">download it on the dedicated page</a>, dowload it in the plugin folder of pluxml and enable it in the admin menu :

[caption id="attachment_497" align="aligncenter" width="584" caption="plugin activation in pluxml"]<a href="http://www.lengrand.fr/wp-content/uploads/2012/01/admin_plugins.jpeg"><img class="size-large wp-image-497" title="plugin activation in pluxml" src="http://www.lengrand.fr/wp-content/uploads/2012/01/admin_plugins-1024x612.jpg" alt="plugin activation in pluxml" width="584" height="349" /></a>[/caption]

&nbsp;

&nbsp;

Lots of <strong>themes</strong> have been created by the community. <strong><a title="pluxml themes" href="http://ressources.pluxml.org/" target="_blank">They can be downlodaded here</a></strong>. To install a theme, dowload the source, unzip it and dowload it to the themes folder of pluxml's root. Finally, choose it in the admin menu (section "display settings").
<em>Final tip :</em> Most of your information are stored in the parametres.xml file available in the data/configuration folder.
You can have an idea of what pluxml can give <a title="pluxml test" href="http://www.lengrand.fr/pluxml/513/" target="_blank">here ( on my sample server)</a> or in <a title="websites powered by pluxml" href="http://wiki.pluxml.org/index.php?page=Sites+r%C3%A9alis%C3%A9s+avec+PluXml " target="_blank">the list of websites powered by Pluxml</a>!

Enjoy, and let me know if you need any french translation!
