---
layout: post
status: publish
published: true
title: My experience at the 2017 Polymer Summit
author: Julien Lengrand-Lambert
author_login: jlengrand
author_email: julien@lengrand.fr
author_url: http://www.lengrand.fr
categories:
- work
- job
- development
tags:
- front-end
- polymer
- ing
- work
- startup
comments: []
---
Last week, I attended my first conference ever : The 2017 Polymer Summit in Copenhagen. 

I am used to go to Meetups (and organize them [myself](http://meetup.com/Saturday-Morning-Coding-Utrecht)) but it was my first time taking part in something at a bigger scale. 
  


Since I joined [ING](http://ing.nl), I have been focusing pretty much only on front-end development, and more specifically [Polymer](http://polymer-project.org). It was a pleasure to be able to hear more about it from the founding team itself.
With my majestic 3 months experience with Web Components, I really felt like a baby talking to people that **created the standard**.


Most of the talks were very interesting, and the annoucement of Polymer 3 (and the switch to Javascript modules!) was a good (and hoped for :D) surprise. You can find all of them on [Youtube](http://www.youtube.com/watch?v=TDpiyrcOO30&list=PLNYkxOF6rcIDP0PqVaJxqNWwIgvoEPzJi), and I recommend most of them if you are interested in Polymer, or by web components in general. 


After a couple months working with Polymer, my feeling going to the conference was a bit saur:

* HTML imports were still not a thing in browser, forcing us to use polyfills.
* Polymer came with its own toolchain, which kinda forced you to acquire specialized (but not so relevant IMHO) knowledge.
* The clear trend (looking at Angular 2, React, VueJs, ...) was clearly not with HTML files, but Javascript modules.
* Using a deprecated package management, and in general 'outdated' ways of doing.


I felt like Polymer was an interesting technology, which I really appreciated but was destined to die slowly by lack of adoption. It just failed to gain traction. 
A simple way to see this is to try to build side projects in Polymer, and see [the number of] [deprecated] or [half-dead components].


Now, the first announcements got me really excited!

* Switching to Yarn, the latest trend in package management
* No more HTML imports, but ES modules instead. Thus no need for polyfills any more (at least to support HTML imports).
* It should now be possible to leverage main technologies such as webpack, template literals, . . . and can be reused in other areas too.


I feel like the leading team clearly listened to the community and took action to give Polymer a chance. Clearly they still think that their original approach was more elegant and better. However, it is appeciated to see that they are ready to let go of their convictions for the well-being of the project. Now, I am convinced that Polymer has a brighter future that it did a couple weeks ago. 


**The large advantage, in my opinion, that Web Components based frameworks have compared to other approaches that lately have more traction (say VueJs or React) is the presence of the shadow/shady DOM**. 
This unpiercable layer allows you to stay unconcerned about changing technology in the future : **All of your components will be compatible with whatever new approach you are choosing**. You can decide to replace them as you go.
Said a other way, all of the web components available on webcomponents.org can be used by anyone in any setup. Can't quite say the same about React modules by example.


Finally, I wanted to share my feeling at the end of the summit. I have to say it was very energizing to hear stories from such inspiring people. The common trait of all of the speakers there was their **take it, own it and solve it** mentality. It is something that I felt I had lost a bit over the last couple of years. 


I am now coming back full of energy, ready to tackle my next project. And this project will be in Polymer :).

