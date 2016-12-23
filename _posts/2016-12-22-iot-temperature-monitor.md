---
id: 244
title: IOT temperature monitor
date: 2016-12-22
author: Jorden
layout: post
guid: http://jordenlowe.com/?p=244
permalink: /2016-12-22-iot-temperature-monitor
categories:
  - raspberry pi
  - c
  - iot
  - node.js
  - html
tags:
  - iot
  - node.js
  - c
  - raspberry pi
  - html
---

If you head over to https://github.com/supermitsuba/TemperatureMonitor you will see a temperature monitor system.  My daughter's room was getting cold, so my engineer brain kicked in.  I had raspberry pi's laying around, so that was no problem.  Then I headed over to [adafruit](https://www.adafruit.com/) to pick up a temperature sensor.  I had a wifi adapter, and a couple of wires, so I was all set to build this out.

I created a mysql database to house the data.  Any database would do.  I used docker so that it would allow me to deploy super easy.  Within minutes I had a full working database.  Next, I needed an API to dump data into the database, that's where node.js comes in.  Not only did I use node, but I used Typescript on top of that.  Typescript gives static typing to javascript, which is useful for catching spelling and casing bugs.

On the client side, I created a node script and a c executable.  The c executable uses wiring PI to poll the temperature.  The node script calls the c executable and posts the data to the database.  The reason I did this in node is that it is easier to call a web api in node than c.  The only issue I ran into was that node would receive the data in a large chunk, instead of as the readings come in.  This is ok, cause I can get the average of each chunk and that will save me space in the database.  I dont need the readings down the the second, just something to see over time.

So, after that, here are the images:

![raspberry pi](/wp-content/uploads/2016/1.jpg)
![website](/wp-content/uploads/2016/2.jpg)

For the web site, I used [twitter bootstrap](http://getbootstrap.com/) and [chart.js](http://www.chartjs.org/).  This gives it a decent way to view the graphs, even on a mobile device.
