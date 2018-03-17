---
layout: post
status: publish
published: true
title: Participating the Green Hackfest Utrecht 2014
author: Julien Lengrand-Lambert
author_login: jlengrand
author_email: julien@lengrand.fr
author_url: http://www.lengrand.fr
categories:
- hackathon
- development
tags:
- sustainability
- charging pole
- electric car
comments: []
---

Hey there,

Writing today about something that happened a loooong time ago but I just finally received a digital copy of the article so it felt relevant :).

About a year ago, I participated with friends to the Green Hackfest in Utrecht. The challenge was to modernize electric chargers in urban areas, the idea being that those chargers are popping up everywhere due to the increasing numbers of electric vehicles in cities. We had to take the current product, and see what more could be done with it using smart sensors. Pretty generic, but interesting nevertheless!

We decided to focus on the fact that electric vehicle owners were contributing to the reduction of urban pollution, since they are rejecting less CO2 in the atmosphere. We wanted to make a "celebration" out of this, and show a growing "tree of life" using LEDs as the charger was being used. In addition, CO2 sensors would be used in the chargers so they can also be used as a proximity check for neighbors to see the quality of the air they breathe. Finally, the idea was to also incentive communication by informing people as soon as their car has finished charging so they can let the spot free for one of their neighbors.

We had a very diverse team, which allowed us to use a lot of different technologies :

* A raspberry pi was used to simulate the charging poles, with a wide variety of sensors

* An Arduino was used to simulate the growth of the "tree of life" over time, as people save CO2 using their electric car

* A server, running a Ruby On Rails app was used to host a REST API with simple storage and retrieval of the sensor values over the different charging poles for the experiment. This would later on be used to generate "heatmaps" of CO2, Air quality, ....

* An android app, used to give information about the sensors in the neighborhood and receive notifications when the car has finished charging.

You can find some more information about the concept [in this PDF](http://dl.dropboxusercontent.com/u/4286043/00_Website/03_Images/green-hack/Hackathon.pdf), and a screenshot of the running web app [here](http://dl.dropboxusercontent.com/u/4286043/00_Website/03_Images/green-hack/web.png).

We did not end up winning the Hackathon, but we did win the "Visualizing Sustainability" challenge from the event.

![The winning team after the event](http://dl.dropboxusercontent.com/u/4286043/00_Website/03_Images/green-hack/IMG_4472.JPG)

A couple weeks later, a meeting was organized in Utrecht with the partners that were responsible for this challenge : the EBU Climate KIC and LomboXNet. We did not pursue the idea further after the hackathon, but our work was used as input for further upgrade of the charging poles. [**You can find a link to the article published in the EBU Mag here**](http://dl.dropboxusercontent.com/u/4286043/00_Website/02_Articles/ebu_mag_09_interview_slimme_laadpaal.pdf).

All in all, it was a really fun event and the overlapping expertise from the team allowed us to get a lot done in only 2 days!

