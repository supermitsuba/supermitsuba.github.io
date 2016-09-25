---
id: 69
title: Programming Serial with C Sharp
date: 2013-03-11T12:00:00+00:00
author: Jorden
layout: post
guid: http://www.fbombcode.com/title/Programming_Serial_with_C_Sharp
permalink: /2013/03/11/programming-serial-with-c-sharp/
categories:
  - .net
  - electronics
tags:
  - .net
  - c
  - electronics
  - serial
---
 <p> I have been programming for my Ardunio and Raspberry PI. For the Ardunio, I have connected to my Raspberry PI through USB. Once I got the Ardunio drivers working, now I can communicate from the Raspberry PI, through Serial. Although there are multiple avenues on communicating with the Ardunio, I decided to load up mono on the Raspberry PI and use .Net to communicate to the Ardunio. Here is how I did it. </p> <p> Let�s start with initializing the serial port: </p> <figure> <code> <img src ="/img/14.png" /> </code> </figure> <p> CreateSerial creates a serial port with a port on your computer. If you are wondering if it works with mono, THEN YES IT DOES. Now because mono doesn�t give the same names to ports as windows, I put a console.writeline there to get an idea of what ports I have available to connect. After you pick a port, the rest is just standard stuff that is associated with communicating serial to an Ardunio. Stuff like, BaudRate, DataBIts StopBits and etc. </p> <p> The important things to note are the following: <ol> <li> serialPort.DataReceived </li> <li> serialPort.WriteLine </li> </ol> </p> <p> These 2 functions are the ways to communicate with the serial port. First, the DataReceived function, we need a call back to handle the event of when the serial port has received data: <div> <figure> <code> <img src ="/img/15.png" /> </code> </figure> </div> Then we can just call WriteLine as we want to write data to the serial port we want to use. The main program can be as simple as this : <div> <figure> <code> <img src ="/img/16.png" /> </code> </figure> </div> </p> <p> Now you can send and receive data from a serial port relatively easy. Do note, you will need to close the port, otherwise you will block other software from accessing the port, but that�s an easy close function call. This is what I used to communicate with an Ardunio to give it messages, and it was super easy. In a later article, I�ll go over how I used this in my Arudino project. </p>