---
layout: post
status: publish
published: true
title: A simple way to get a multilingual blog
author: Julien Lengrand-Lambert
author_login: jlengrand
author_email: julien@lengrand.fr
author_url: http://www.lengrand.fr
wordpress_id: 366
wordpress_url: http://www.lengrand.fr/?p=366
date: 2011-12-12 13:55:52.000000000 +01:00
categories:
- tips
tags:
- pluxml
- javascript
- website
- language
- multiingual
- html
comments:
- id: 87
  author: Mike
  author_email: mike@mike.cim
  author_url: ''
  date: !binary |-
    MjAxMS0xMi0xMiAyMDo0Njo1OCArMDEwMA==
  date_gmt: !binary |-
    MjAxMS0xMi0xMiAxOTo0Njo1OCArMDEwMA==
  content: Ugh JavaScript, that is a terrible solution. Use JS to add interaction,
    don't use it to show/hide information. Use separate pages, with their own language
    tag and their own URL. The internet will thank you, and so will people using screen
    readers!
- id: 88
  author: Julien Lengrand-Lambert
  author_email: julien@lengrand.fr
  author_url: http://www.lengrand.fr
  date: !binary |-
    MjAxMS0xMi0xMiAyMTo0ODowNiArMDEwMA==
  date_gmt: !binary |-
    MjAxMS0xMi0xMiAyMDo0ODowNiArMDEwMA==
  content: ! "I agree on the fact that this is not the best trick ever used. As you
    say, javascript should not be used to hide information. \r\n\r\nThere are some
    pros though. My first idea in creating the blog was to have two templates and
    separate pages. The thing is that it is the same as creating two different blogs.
    You have twice as much updates to perform, with half references. . . \r\n\r\nI
    think Javascript might be used in case you have a \"prefered\" language, and make
    another available \"as a gift\" for people."
---
<!--:en-->Hi all,

Some time ago, I searched for a way to have a blog as simple as possible (and avoid <strong>wordpress</strong> or <strong>joomla</strong> monsters). I ended up using <strong><a title="pluxml" href="http://www.pluxml.org/">Pluxml</a></strong> for a while, and you can find<a title="pluxml here" href="http://www.lengrand.fr/pluxml/513/"> the result here</a><a title="pluxml here" href="http://www.lengrand.fr/pluxml/513/">.</a>

One of the things I wanted absolutely was to <strong>write my blogs in several languages</strong> (french and english). After some time, I finally found a way to do it with a bit of <strong>javascript</strong>.

The main idea is simple : You get one <a title="div" href="http://www.w3schools.com/tags/tag_div.asp" target="_blank">div</a> by language. On startup, only one div is shown, and a click on a "switch language" link shows the other div while making the first disappear.

You can see an <a title="result multilingual" href="http://lengrand.fr/pluxml/513/index.php?article2/new-article" target="_blank">example of the result </a><strong><a title="result multilingual" href="http://lengrand.fr/pluxml/513/index.php?article2/new-article" target="_blank">here</a>.</strong>

To do this, you need two things :
<ul>
	<li>Insert some <strong>javascript</strong> functions in your webpage. You can do this by importing a file, or simply copying the following code in your template:</li>
</ul>
<div>[javascript]

&lt;!-- Script créé par KevBrok ;-) --&gt;
&lt;script type=&quot;text/javascript&quot;&gt;// &lt;![CDATA[
	/*
	* Montre / Cache un div
	*/
	function DivStatus( nom, numero )
		{
			var divID = nom + numero;
			if ( document.getElementById &amp;&amp; document.getElementById( divID ) ) // Pour les navigateurs récents
				{
					Pdiv = document.getElementById( divID );
					PcH = true;
		 		}
			else if ( document.all &amp;&amp; document.all[ divID ] ) // Pour les veilles versions
				{
					Pdiv = document.all[ divID ];
					PcH = true;
				}
			else if ( document.layers &amp;&amp; document.layers[ divID ] ) // Pour les très veilles versions
				{
					Pdiv = document.layers[ divID ];
					PcH = true;
				}
			else
				{

					PcH = false;
				}
			if ( PcH )
				{
					Pdiv.className = ( Pdiv.className == 'cachediv' ) ? '' : 'cachediv';
				}
		}

	/*
	* Inverse les divs: Cache les divs visible et montre le divs cachés :)
	*/
	function InverseTout( nom )
		{
			var NumDiv = 1;
			if ( document.getElementById ) // Pour les navigateurs récents
				{
					while ( document.getElementById( nom + NumDiv ) )
						{
							SetDiv = document.getElementById( nom + NumDiv );
							DivStatus( nom, NumDiv );
							NumDiv++;
						}
				}
			else if ( document.all ) // Pour les veilles versions
				{
					while ( document.all[ nom + NumDiv ] )
						{
							SetDiv = document.all[ nom + NumDiv ];
							DivStatus( nom, NumDiv );
							NumDiv++;
						}
				}
			else if ( document.layers ) // Pour les très veilles versions
				{
					while ( document.layers[ nom + NumDiv ] )
						{
							SetDiv = document.layers[ nom + NumDiv ];
							DivStatus( nom, NumDiv );
							NumDiv++;
						}
				}
		}
// ]]&gt;&lt;/script&gt;
[/javascript]

</div>
<ul>
	<li>Then, <strong>Write down your article in both languages</strong>, one after the other in you editor. Each language should be placed in a separate div; and a button placed to switch from one language to the other. Here is an example :</li>
</ul>
<div>[javascript]
&lt;a href=&quot;javascript:InverseTout( 'mondiv' )&quot;&gt;Français / English&lt;/a&gt;&lt;/pre&gt;
&lt;div id=&quot;mondiv1&quot; class=&quot;cachediv&quot;&gt;
&lt;div style=&quot;border: 1px solid black; background-color: whitesmoke; margin-bottom: 2px;&quot;&gt;My article in english&lt;/div&gt;
&lt;/div&gt;
&lt;div id=&quot;mondiv2&quot;&gt;
&lt;div style=&quot;border: 1px solid black; background-color: whitesmoke; margin-bottom: 2px;&quot;&gt;Mon article en français&lt;/div&gt;
&lt;/div&gt;
&lt;pre&gt;
[/javascript]

</div>
<div>

There you are ! The<strong> "class = cachediv"</strong> is used to hide the on load.

</div>
All you have to do now is to "beautify" the code by changing the link into a flag, and enhance the way div are displayed.The bad thing is you will have some javascript code in your articles, and both languages are present on the same page.

Hope this help ;)
<div>

<strong>And if you have a better idea, please let me know !</strong>

</div>
<div>[<a title="source" href="http://www.editeurjavascript.com/scripts/scripts_navigation_3_182.php" target="_blank">source</a>]</div>
<div><em>NOTE : Sorry for the code being in french (its not mine). I could take some time to translate it if you want :) </em></div><!--:-->
