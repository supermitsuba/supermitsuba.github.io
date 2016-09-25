---
id: 56
title: Underscore.js
date: 2013-06-30T00:00:00+00:00
author: Jorden
layout: post
guid: http://www.fbombcode.com/title/Underscore.js
permalink: /2013/06/30/underscore-js/
categories:
  - javascript
  - node.js
  - web
tags:
  - javascript
  - node.js
  - underscore.js
  - web
---
 <p> Expressing things in a functional way sometimes is easier than a procedure way. Underscore gives you that flexibility and really simplifies data processing. </p> <p> A while back I created an article about using <a href="/title/Linq,\_Now\_in\_Javascript\_flavor">Linq in javascript</a>. Well, there is another library for doing similar things, <a href="http://underscorejs.org/">Underscore.js</a>. Originally part of backbone, but split away to become a utility library instead. This library fits well with jQuery and backbone, so using the library won&#8217;t conflict. This library also enhances jQuery&#8217;s already functional nature, keeping your code much more terse. Let&#8217;s see how it fits in: </p> <pre class="formatCode"> var largest = 0; var number = 0; var start = Date.now(); for(var i = 2; i < 1000000; i++) { var length = Collatz(i); if( largest < length) { largest = length; number = i; } } var end = Date.now(); console.log("The largest: "+largest+" The number: "+number); console.log("ms: "+ (end-start)); function Collatz(value) { var number = value; var length = 1; while(number != 1) { if(number%2==0) { number=number/2; } else { number = 3\*number+1; } length += 1; } console.log("value: "+value+" length: "+length); return length; } </pre> <p> So, here is the solution to problem 14 in <a href="/title/Learning\_JavaScript\_with_Euler">project Euler</a>. While this looks fine, let's tweak it a little with Underscore: </p> <pre class="formatCode"> var u = require('underscore'); var largest = 0; var number = 0; var start = Date.now(); u.each(u.range(2, 1000000),solve); function solve(value) { var length = Collatz(value); if( largest < length) { largest = length; number = value; } } var end = Date.now(); console.log("The largest: "+largest+" The number: "+number); console.log("ms: "+ (end-start)); function Collatz(value) { var number = value; var length = 1; while(number != 1) { if(number%2==0) { number=number/2; } else { number = 3\*number+1; } length += 1; } console.log("value: "+value+" length: "+length); return length; } </pre> <p> The biggest thing I saw when removing the loop, was it actually made the code simpler. Think about it, removing the for loop makes the code much easier to read and brings the code complexity down. The advantage of functional programming is processing data. Try out underscore, and see if it may help. </p>