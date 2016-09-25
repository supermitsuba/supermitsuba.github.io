---
id: 68
title: Turn crappy text into code for HTML
date: 2013-03-17T00:00:00+00:00
author: Jorden
layout: post
guid: http://www.fbombcode.com/title/Turn_crappy_text_into_code_for_HTML
permalink: /2013/03/17/turn-crappy-text-into-code-for-html/
categories:
  - HTML
  - javascript
  - web
tags:
  - html
  - javascript
  - web
---
 <p> So I have been using images for all my code examples. While they are great, it is a pain in the ass to create for each resolution level. Mind you, I have not created different sized images, but I wanted something that would be as easy as text, but show up well all around. That’s when I started playing with <a href="https://code.google.com/p/google-code-prettify/" >google-code-prettify</a>. </p> <p> This is the same code styling that Stack Over flow uses and is hosted by google. It’s pretty awesome, because it is literally as easy as adding a few css and js files and off we go. Here is an example: </p> <pre class="formatCode"> <!--first add this--> <link href="../css/prettify.css" type="text/css" rel="stylesheet" /> </pre> <p> Then in your site’s javascript file add these few lines: </p> <pre class="formatCode"> jQuery.fn.prettify = function () { this.html(prettyPrintOne(this.html())); }; $(document).ready(function () { $('.formatCode').prettify(); } </pre> <p> This code basically just says, where ever you see a css class of &#8220;formatCode&#8221;, make it look like code. Now lastly, you probably want to use a pre tag, as a pre tag will keep the whitespace and line delimiters, and boom, you have some awesome looking code. </p> <pre class="formatCode"> <pre class="formatCode"> <!--first add this--> <link href="../css/prettify.css" type="text/css" rel="stylesheet" /> </pre> <p> HAHA that last bit of code for me was like inception. Now some of the other issues I ran into with this were that I had to escape all the html characters, but otherwise, it should format great. I’m hoping this article looks good in a rss reader, so I can just use this method, instead of images…but I’m not holding my breathe. I’ll post a follow up in the comments later to let you guys know. </p>