---
layout: post
status: publish
published: true
title: Strange bug with long XML files in android.
author: Julien Lengrand-Lambert
author_login: jlengrand
author_email: julien@lengrand.fr
author_url: https://www.lengrand.fr
wordpress_id: 912
wordpress_url: https://www.lengrand.fr/?p=912
date: 2014-01-29 09:51:46.000000000 +01:00
categories:
- brestram
- android
tags:
- android
- xml
- brestram
- java
- update
comments: []
---
Lately I encountered a strange bug while developing my <a title="brestram main page" href="https://play.google.com/store/apps/details?id=fr.lengrand.brestram&amp;hl=en" target="_blank">android</a> application, and I think it is strange enough to share it in this blog post.

<strong><a title="brestram main page" href="https://play.google.com/store/apps/details?id=fr.lengrand.brestram&amp;hl=en" target="_blank">Brestram</a></strong> is an android application that aims at delivering real time bus schedule for the people living in <a title="google maps brest" href="https://maps.google.com/maps?hl=en&amp;q=maps+brest&amp;ie=UTF-8&amp;hq=&amp;hnear=0x4816bbe1d9925b93:0xc6488358179c30ab,Brest,+France&amp;ei=QqDmUrHnM8mm0AW274HQCQ&amp;ved=0CCoQ8gEwAA" target="_blank">Brest</a>.
For each new version,  I want to display a small message with the new features of the version.
I need to deliver the message both in English and in French, and I wanted to keep history of all the messages I have written in the past for reference.
On top of this, I wanted to be able to write that message in an understandable format (for me) to avoid formatting errors.

I decided to go for XML, for all the reasons above, and also because android supports it really well out of the box.

Here is how my update file would look like :

{% highlight xml %}

<?xml version="1.0" encoding="utf-8">
<resources>
<!-- This file contains all the update messages displayed to the user-->
<!-- To create a new update message:
- Create a new update array, with a incremented update number
- Add a reference to this new array in the updates array
-->

<!-- Template is : -->

<!--
<array name="update0">
<item>update title</item>
<item>update message</item>
</array>
-->

<string-array name="update0">
<item>
"Mise à jour du site Bibus"
</item>
<item>
"Bibus a récemment changé son protocole de communication pour les horaires temps réel.\n
Il est donc en ce moment impossible pour BresTram de fonctionner correctement.\n
(Merci Lucas de m'avoir prévenu!)\n
Ceci est totalement indépendant de BresTram, et je fais mon possible pour corriger ceci au plus vite!\n
En attendant, si vous trouvez l'application utile, aidez-moi en votant sur le play store!\n
Merci d'avance, et désolé pour le dérangement."
</item>
</string-array>
. . .

<array name="update12">
<!-- French -->
<item>
"Mise à jour du 27 Janvier"
</item>
<item>
"BresTram vient d'être mis à jour.\n\n"
"Un nouvel onglet a été ajouté pour vous permettre de faire des recherches par ligne de bus.\n"
"Il vous est maintenant possible de voir la liste de toutes les lignes possibles dans l'onglet lignes.\n\n"
"Cette nouvelle fonctionnalité est pour le moment encore en beta, il est donc possible que vous rencontriez des bugs."
"Faites moi part de vos remarques sur le play store où sur le Twitter de l'application!"
</item>
<!-- English -->
<item>
"BresTram was updated to version 1.5"
</item>
<item>
"BresTram has been updated to the latest version.\n\n"
"A new tab has been added, that lists all bus lines and their associated bus stops.\n"
"This functionality is currently still in beta, and you might find bugs.\n\n"
"Let me know your suggestions on the playstore or the twitter of the application!"
</item>
</array>

<!-- Array containing a reference to all the messages -->
<array name="updates">
<item>@array/update0</item>
. . .
<item>@array/update12</item>
</array>
</resources>

{% endhighlight %}

Basically, my update mechanism rely on two different things :
<ul>
	<li>A large group of XML arrays</li>
</ul>
Each array describes one update. Each of those updates is divided into 4 items : a title and a content, in English and then in French.
<ul>
	<li>Then, another array lists all the update messages.</li>
</ul>
Each item of the array contains a reference to an update, in ascending order.

To use this file, <strong>I wrote a small update functionality in Java</strong> (that may be the subject of a future blog post).
The updater <strong>compares the value of the latest update</strong> <strong>with the current version number in database</strong>, and displays the update message if needed.

But basically, the java code of interest can be summarized in the few following lines :

{% highlight java %}
 private Resources res;
 // gets a reference to the array of updates
 res = ctx.getResources();
 private TypedArray update_messages = res.obtainTypedArray(R.array.updates);

// do useful stuff with the typed array. For example, get the total number of updates available :
 /**
 * Returns the latest version number of the application.
 * This gives the number of update messages in the updates file
 * @return the latest version number
 */
 public int getLatestVersion(){
 return update_messages.length();
 }
{% endhighlight %}


But for some strange reason, things started acted weird last month. <strong>My 11th update wouldn't show up. Instead, it was the 8th being displayed!</strong>

I checked the format of the xml times for a while, screening for a silly copy-pasting error or something alike. But I couldn't find anything.

After some time, I started checking my Java code. During the debugging,<strong> I realized that my update array was detected as 8 rows long, instead of 11.</strong>
At least I had found the reason why another update was showing up on screen instead of the one I was waiting for. <em>But why?!</em>

I kept searching for a while, realizing that <strong>everything was for example working fine if I was replacing the text of my 11th update by a copy of my 10th update message . . .</strong>

Tired of not being able to find the source of the problem, I started trying things that made no sense. And I finally realized that<strong> if I put the array containing the list of references to my updates BEFORE that actual updates, everything was fine.</strong>

I guess for some reasons the amount of data read by the xml parser is limited. When creating the typed array, only a fixed amount of data is grabbed from the xml resource file. When the number of updates grew, the xml file started being too long and I finally ended up grabbing only part of my array.

So basically, I am now 4 updates later, and things continue to behave normally, so I guess the problem is "fixed".
So far, I am still searching for a proof of these assumptions though. . .
In case you know the exact reason why this happened, feel free to drop me a line in the comments of reach me on <a title="my twitter" href="https://twitter.com/jlengrand" target="_blank"><strong>twitter</strong></a>.
