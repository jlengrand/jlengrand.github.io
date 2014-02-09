---
layout: post
status: publish
published: true
title: Sonar images segmentation and classification fusion
author: Julien Lengrand-Lambert
author_login: jlengrand
author_email: julien@lengrand.fr
author_url: http://www.lengrand.fr
wordpress_id: 250
wordpress_url: http://www.lengrandlambert.fr/wordpress/?p=250
date: 2012-05-13 13:54:30.000000000 +02:00
categories:
- Computer Vision
- Matlab
tags:
- image processing
- matlab
- classification
- sonar
- segmetnation
- level sets
- publication
- ecua
- egc
comments: []
---
Today's article will present one of my former experience that led to two publications in european conventions.
It dealt with automatic <a title="segmentation wikipedia" href="http://en.wikipedia.org/wiki/Segmentation_(image_processing)" target="_blank">segmentation </a>and <a title="classification wikipedia" href="http://en.wikipedia.org/wiki/Classification_in_machine_learning" target="_blank">classification </a>of sonar images.

It has become really easily nowadays to precisely <strong>keep track of a precise position on a map</strong>; using satellite or aerial images and ground control points that are known to stay still over time.
This is <strong>completely different underwater</strong>, where the<strong> environment constantly changes</strong>, and the number of ground control points is dramatically reduced (wrecks, huge rocks, . . . ). In addition, the bottom of the sea tend to be very uniform compared to ground surface.
In order to solve this issue,<strong> scientists tend to focus on edges between surfaces</strong>, limits between sand zones and pebbles for example.

And the ideal would be to be able to accurately and fully automatically find those edges, together with the type of each surface. Using such a method would allow to create precise maps of the sea floor at reduced costs.

But this problem is way more complex that it seems, especially if you consider that<strong> the edges between surfaces change with time</strong> !
In fact, even humans struggle to get the same results whith manual classification.

If have been working on this subject for a bit less than 6 months, which means that this publication is<strong> a preleminary study</strong> aiming at helping further development.
In this paper, I present a new method that merge a  <strong>feature based classification</strong> which involves a training with <strong>an edge focused method</strong>.
As a basis for the region based algorithm, I used the<a title="level sets wikipedia" href="http://en.wikipedia.org/wiki/Level_set_method" target="_blank"> level-sets method</a>.
With one part of the algorithm searching for homogen zones and the other searching for limits, one can hope to get nice results once merged !

<strong><a title="GESMA_EGC" href="http://dl.dropbox.com/u/4286043/00_Website/01_Publis/Fusion_GESMA_EGC.pdf" target="_blank">Here is a link</a></strong> to the french version of the paper, presented at the <a title="EGC2010" href="http://www.projets.rnu.tn/egc2010/" target="_blank">"10ème Conférence Internationale Francophone sur l'Extraction et la Gestion des Connaissances (EGC)"</a>

<strong><a title="GESMA_ECUA" href="http://dl.dropbox.com/u/4286043/00_Website/01_Publis/Fusion_GESMA_ECUA.pdf" target="_blank">The english version</a></strong> was presented one year later at<a title="ECUA 2010" href="http://www.eaa-fenestra.org/event-calendar/list_of_events/2010/event.2009-06-30" target="_blank"> "10th European Conference on Underwater Acoustics (ECUA) 2010"</a>.
Just for the beauty of it, I want to quickly present some results :
Here is an example of sonar image manually segmented by two different experts. Observe how the results are similar, but also different at the same time.

<a href="http://dl.dropbox.com/u/4286043/expert.png"><img class="aligncenter" src="http://dl.dropbox.com/u/4286043/expert.png" alt="" border="0" /></a>

Here are the results I got using my fully automated method :

<a href="http://dl.dropbox.com/u/4286043/algo.png"><img class="aligncenter" src="http://dl.dropbox.com/u/4286043/algo.png" alt="" border="0" /></a>

Results are actually<strong> quite promising</strong>, given the amount of time I have been working on the subject! (You can have some precise results in the paper)
I just hope that this work will be used later and lead to even more interesting results !

I plan on releasing the code I developed for this project on GitHub. I'll have to clean it up first, though :)
Hope some of you will be interested
See you soon !

Thanks to <strong><a title="arnaud martin" href="http://www.arnaud.martin.free.fr/" target="_blank">Arnaud Martin</a></strong>, <a title="ensta bretagne" href="http://www.ensta-bretagne.fr/" target="_blank">ENSTA Bretagne</a> for having been a helpful teacher; and to <strong>Romain Courtis</strong>, <a title="gesma" href="http://www.defense.gouv.fr/dga/la-dga2/expertise-et-essais/gesma" target="_blank">GESMA </a>for his support.
