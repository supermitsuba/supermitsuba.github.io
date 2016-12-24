---
id: 184
title: LED Bulletin Board
date: 2013-07-14T15:55:38+00:00
author: Jorden
layout: post
guid: http://jordenlowe.com/?p=184
permalink: /2013/07/14/led-bulletin-board/
categories:
  - Projects
tags:
  - .net
  - arduino
  - electronics
---
<div>
  <p>
    Created bulletin board using ardunio, raspberry pi, and some programming know-how to create a mini programmable billboard.
  </p>
  
  <p>
    The creation of this item started out with a <a href="http://www.raspberrypi.org/">Raspberry PI</a>. With a Raspberry PI, it has an arm processor that you can use a debian based linux called Raspbian. The easiest way to get the OS on there is by using <a href="http://www.berryterminal.com/doku.php/berryboot">berry boot</a>. Berry Boot is a boot loader that automatically downloads the image of various linux distros and puts them on your Raspberry PI.
  </p>
  
  <p>
    After the Raspberry PI, I looked for a project to start working on with the mini computer. Someone had made mention to do a LED sign, so I said sure. But that sounded simple, maybe I should throw in a way to send it messages, and for it to get messages. So I started to look into the hardware materials. I got most of the electronics from <a href="http://www.element14.com/">Element14</a> and <a href="http://www.adafruit.com/">AdaFruit</a>. Each site had great tutorials about how to get started, and I found out that I would need another circuit to help ease everything. The other circuit I got was an arduino. So all together I got these parts:
  </p>
  
  <pre>List of parts
1)Raspberry PI
2)Arduino
3)<a href="http://www.adafruit.com/products/555">(4) 16x24 LED Panel</a>
4)<a href="http://www.adafruit.com/products/556">some chain cables to connect the boards together</a>
5)Crap load of Legos
</pre>
  
  <p>
    If you go to Lady Ada&#8217;s <a href="http://ladyada.net/products/16x24LEDmatrix/">site</a>, there is a tutorial of how to connect the LED&#8217;s together and even a how to on how to get it connected to the Arduino. After some retooling, I was able to program the Ardunio to control the LED board through a serial port. This is where the Arduino shines, as it was very easy to get communication going for the <a href="http://jordenlowe.com/2013/04/06/going-back-to-c-programming-with-arduino/">serial bus</a>. Now that I got the serial portion done, it was easy to create a <a href="http://jordenlowe.com/2013/03/11/programming-serial-with-c-sharp/">.Net</a> program, using mono, to display values on the LED sign.
  </p>
  
  <p>
    So for now, it works fine, but I plan to use Node instead, to expose a restful web service to send messages and to update the board with information. Here are some pictures:
  </p>
  <img src="/wp-content/uploads/2016/led.jpg" width="200">
  <p>
  <h2>UPDATE!</h2>
  <p>
    <p>Here is the server source code for the led sign:  <a href="https://github.com/supermitsuba/SMSpiService" >server</a></p>
    <p>Here is the client source code for the led sign:  <a href="https://github.com/supermitsuba/SMSpi" >client</a></p>
    <p>Arduino source code coming soon.</p>
  </p>
  </p>
</div>
