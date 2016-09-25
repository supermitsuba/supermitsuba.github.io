---
id: 71
title: Responsive UI in a few minutes
date: 2013-03-10T12:00:00+00:00
author: Jorden
layout: post
guid: http://www.fbombcode.com/title/Responsive_UI_in_a_few_minutes
permalink: /2013/03/10/responsive-ui-in-a-few-minutes/
categories:
  - HTML
  - javascript
tags:
  - html
  - javascript
---
 <p> Making websites go through phases. First we had just HTML and it was good. Then someone added some cgi to get dynamic pages to work. After that, javascript was added and was depressing to implement all the versions of browsers. Now, just when you think javascript handles all the different browsers and configurations, then comes it different screen sizes with mobile browsers. Here with this article, I want to show some ideas I found to help with formatting for different sized browsers. It may help you get a bigger audience with a few tweaks to CSS3. </p> <p> It�s as easy as css3 media query. I found there were 2 queries, and each one has its purpose. The first query type: screen-width, is useful for the actual browser size and reshaping the websites for that. But for a phone screen, it doesn�t work well to tell us that this screen is smaller. You need to rely on the device-width property. <p> <figure> <code> <img src ="/img/6.png" /> </code> </figure> </p> </p> Here, we have a screen that shows, if the device width is over 768 pixels, then use these css settings, else, if it is between 480 and 768, use these settings: <p> <figure> <code> <img src ="/img/7.png" /> </code> </figure> </p> And lastly, if the screen is smaller than 480 pixels, then do this: <p> <figure> <code> <img src ="/img/8.png" /> </code> </figure> </p> That�s it, now we can control the display of content based on the device width. This site knocks off the tabs on the side, and adds 2 new menu items when viewed on the phone. This makes viewing less of a scroll fest and allow the viewer to read the page with minimal interference.