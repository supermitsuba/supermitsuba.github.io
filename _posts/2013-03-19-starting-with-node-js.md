---
id: 67
title: Starting with Node.js
date: 2013-03-19T00:00:00+00:00
author: Jorden
layout: post
guid: http://www.fbombcode.com/title/Starting_with_Node.js
permalink: /2013/03/19/starting-with-node-js/
categories:
  - javascript
  - node.js
tags:
  - javascript
  - node.js
---
 <p> So, some people asked me to go through a series on Node.js to get them started on their projects. I forgot that in my previous article, I just talked about it at a high level, and did not go through the installation of Node, so let&#8217;s do just that. </p> <p> First go grab the interrupter for Node.js from <a href="http://nodejs.org/">NODE.js</a>. This will allow you to run any javascript in command line, with basic node.js apis. One thing to note, if you grab the stand alone executable (assuming for windows) don&#8217;t forget to add it to your path variable ;-). Next go out and grab this guy here: <a href="https://npmjs.org/doc/README.html#Fancy-Windows-Install">NPM</a>. That is npm, it is like apt-get, or nuget, but for node.js packages. Really important to get both of these to get started. Just like node.js, make sure you add npm to your path variable. </p> <p> Once you have done that, now you can start executing command line arguments like: </p> <pre class="formatCode"> npm install fs </pre> <p> Whoa Jorden, WTF did you just do!1!? NPM just went out and installed fs to my current project. If you wanted to use it globally, use -g at the end like this: </p> <pre class="formatCode"> npm install -g fs </pre> <p> Now that we got that out of the way, now we can write some basic node.js javascript :-). That package we downloaded was to read and write to the file system. Let&#8217;s try to do some of that: </p> <pre class="formatCode"> var myPath = "blah.csv"; var values = GetCSV(myPath); console.log(values); function GetCSV(filePath){ return fs.readFileSync(filePath, 'utf8'); } </pre> <p> So, that code reads a csv file, and prints it out to the screen. Next take that code, save it to a file named test.js and run it in the command line like this: </p> <pre class="formatCode"> node test.js </pre> <p> I think that is it for the easy stuff. I will have to make a new article on a different api later. Write a comment if you want to see something specifically :-). </p>