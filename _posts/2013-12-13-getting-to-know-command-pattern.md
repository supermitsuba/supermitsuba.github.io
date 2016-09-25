---
id: 39
title: Getting to Know Command Pattern
date: 2013-12-13T00:00:00+00:00
author: Jorden
layout: post
guid: http://www.fbombcode.com/title/Getting_to_Know_Command_Pattern
permalink: /2013/12/13/getting-to-know-command-pattern/
categories:
  - general
tags:
  - design patterns
  - gang of 4
---
 <p>Hey guys,</p> <p>I know that the command pattern is a buzz word Jorden throws around in meetings, but I wanted to talk about it to get you guys a better way to illustrate what the command pattern does. So let’s see 🙂</p> <p>There are a few pieces, Receiver, Invoker and the Interface of the Command. Each has a purpose, and altogether they make commands and the object they operate on, loosely coupled.</p> <p>Receivers are like the object state you are changing. A form, a message, or anything else that we want to change in the command. No, Receivers do not need to have Receivers in the name, but it is good to comment about what the Receiver is, if it is not.</p> <p>Invoker is like the thing that manages the commands that come in and provides the way to execute them. In undo or rollback functionality, you would have a queue of all the commands that you executed on, so that way you can go back through them to rollback. This class is just the place where commands are collected and fired. YOURE FIRED!!! <p> <p>Command Interface and all the Implementations are the chunks of code that do the work. Combined with Receiver, they manipulate the state and create the functionality that you need. Typically there is an “Execute” method, but if you want to support Undo, you should also add an undo method to the Interface to implement it.</p> <p>That’s it. I think the <a href="http://en.wikipedia.org/wiki/Command_pattern">wiki article</a> has a good example with the C# code to describe the command pattern, so check it out.</p>