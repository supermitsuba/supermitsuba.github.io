---
id: 72
title: Use HTML Templating for more than just HTML
date: 2013-03-06T12:00:00+00:00
author: Jorden
layout: post
guid: http://www.fbombcode.com/title/Use_HTML_Templating_for_more_than_just_HTML
permalink: /2013/03/06/use-html-templating-for-more-than-just-html/
categories:
  - HTML
  - web
tags:
  - html
  - web
---
 <p> Templating Engines are cool, but why are they F**KING AMAZING!?!?! The reason is you can use them for much more than templating your websites. Whether it is xml, RSS feeds, email templates, letters, you can use templating for ANYTHING and I will show you how. </p> <p> So, the initial thing that makes them awesome is that they allow you to write HTML. <figure> <img src="/img/1.jpg" /> </figure> The pieces you have to remember with templating is that you get it an &#8220;Entity&#8221; or model. In the case above it is &#8220;blog&#8221; . This model is used to provide the dynamic data to generate. The neat things with models is that you can add ANYTHING, property, functions, hell you could even add logic to say if this value is null, then just display &#8220;no blog&#8221; if you wanted. Templates blur the line of business logic and view logic. </p> <p> Great, I got it working in my site, but what else can I do with this templating stuff? What if I told you, you could use that same HTML template and use it to display as an email out to a user: <figure> <img src ="/img/2.jpg" /> </figure> And don&#8217;t stop there, the only reason why I have an RSS feed is that I created a template to post my blog. <figure> <img src ="/img/3.jpg" /> </figure> </p> <p> Now, all those things, I just told you about, you could use with <a href="http://handlebarsjs.com/" >handlebars</a>, <a href="http://embeddedjs.com/">EJS</a> (which I use), <a href="http://jade-lang.com/">Jade</a> and many more. But how does this help me with my programming in server side code? Well, at least for C#, enter <a href="http://razorengine.codeplex.com/">Razor Engine</a> . Razor engine is awesome because now it allows you to defer some code to be executed at runtime. More specifically, I had some issues where we have to deliver documents to many different investors, and each investor has different naming conventions. Razor would allow you to defer programming this until later, WITHOUT STOPING YOUR APP AT ALL. MIND BLOWN!!! Let&#8217;s take a look: <figure> <code> <img src ="/img/4.jpg" /> </code> </figure> Here we show some code that configures a name for a specific user, actually that code would build &#8220;Jorden.tif&#8221;. But what if the client wants us to create a manifest file of all the files that we just named, lets edit some of the code to add a file write: <figure> <code> <img src ="/img/5.jpg" /> </code> </figure> And the beauty of all this, NO CODE CHANGES TO PROD, just change the template you feed it and let it rip. Check it out for yourself and be the judge, you&#8217;ll find out that it is another tool in the tool box for flexible code. </p>