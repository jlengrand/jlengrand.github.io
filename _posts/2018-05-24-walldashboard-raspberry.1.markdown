---
layout: post
status: publish
published: true
title: Creating a wall dashboard with an old laptop screen
author: Julien Lengrand-Lambert
author_login: jlengrand
author_email: julien@lengrand.fr
author_url: http://www.lengrand.fr
categories:
- work
- fun
- development
tags:
- bash
- experiment
- dakboard
- dashboard
- work
- startup
- hack
comments: []
---

Heyo, 

The past year, I've had a growing need for a dashboard to check what's coming. 
Lots of things to take care of for the baby, my girlfriend leaving couple days a month on average, keeping all family visits in mind, but also checking the weather of the day to know how to dress the little one. 
Looks like having a baby requires you to get organized a little more :).

Luckily, I had an old laptop screen laying around for such an occasion, and I had a couple Raspberries on the shelf. So I decided to get to the task. 

## Getting the hardware together

So the first thing to do was to get all the hardware needed for such a project: 

* An old laptop screen
* A raspberry pi, with a power cable
* An inverter kit to convert the LDVS laptop output to HDMI such as [this one](https://www.ebay.com/itm/HDMI-DVI-VGA-Driver-LVDS-Inverter-Kit-Convert-a-Bare-Laptop-LCD-into-Monitor-/111115624120).
* Another power cable to power the screen
* An HDMI cable to connect the screen to the pi

The cool thing with the inverter kit is that it will allow you to control the screen (brightness, on/off, ...).

[Image of the buttons to control the screen]

The inverter kit is pretty simple to connect : 

* One input for the power cable
* One input for the control board
* One input for the actual screen signal conversion.

You just have to be careful to choose the right type of inverter for your screen. 

Once everything is connected, you essentially have a computer in front of you and the next step is to start working on the software side of things. 

## Setting up the Raspberry