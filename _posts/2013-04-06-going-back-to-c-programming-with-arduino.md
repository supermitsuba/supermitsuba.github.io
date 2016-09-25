---
id: 64
title: Going Back to C Programming with Arduino
date: 2013-04-06T00:00:00+00:00
author: Jorden
layout: post
guid: http://www.fbombcode.com/title/Going_Back_to_C_Programming_with_Arduino
permalink: /2013/04/06/going-back-to-c-programming-with-arduino/
categories:
  - electronics
tags:
  - ardunio
  - c
  - electronics
---
 <p>A while back I created a cool project using Raspberry PI, Arduino, led screens, legos, and a bunch of caffeine. What I fashioned was a pretty awesome mini bill board, complete with my ability to change it at will. I been meaning to create an article on how I programmed the Ardunio. Now I have finally sat down to write up what I did.</p> <p> So in order to do something cool that introduced me to a bunch of technologies, I had to know what the Arduino was capable of. Luckily, there is a serial port to communicate. If I go back to my previous article about serial communication titled: <a href="/blog/4" > Programming Serial with C Sharp</a>, I knew if I wanted to create a cool billboard system, I would need to do some serial stuff with the Arduino. </p> <p> The great thing about the Arduino is that it does not leave you with just crappy c libraries. It allows you to use some libraries it has to help the pain of c. One such library is their serial library. </p> <pre class="formatCode"> void setup() { Serial.begin(9600); delay(500); } </pre> <p> Unlike programming in Visual c++ or gcc, you do not have a main function that kicks off everything. The entry point to the program is a setup function. There you create all the logic you need to start. Next, there is another weird function called loop. This is for the embedded system. This is how it processes things over and over and over and &#8230;. you get the idea. Here is an example of some code in the loop: </p> <pre class="formatCode"> void loop() { String content1 = ""; String one, two; char character; while(Serial.available()) { character = Serial.read(); content1.concat(character); } console.log(content1); } </pre> <p> That is a bit of code, but let\`s dissect it really quick. The &#8220;String&#8221; object is built in a library in Arudino\`s IDE, and it works kinda like the STL string library. Then we have a while loop. This reads all available characters from the serial buffer. Once the buffer is depleted, it will kick out of the loop and print what was sent to the console. Super easy. </p> <p> You can get the Arudino IDE here: <a href="http://www.arduino.cc/">http://www.arduino.cc/</a> and if you are looking to buy one, check out Microcenter, or <a href="http://adafruit.com/">Adafruit.com</a>. If you are a little timid about how to get started, visit adafruit, as they have many tutorials on how to do this stuff. But believe me, it is super easy. If you are looking to get an example of how to put these things together, I will have a project article out soon to describe it all, so stay tuned. 🙂 </p>