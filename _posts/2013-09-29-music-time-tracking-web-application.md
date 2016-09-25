---
id: 189
title: Music Time Tracking Web Application
date: 2013-09-29T15:59:35+00:00
author: Jorden
layout: post
guid: http://jordenlowe.com/?p=189
permalink: /2013/09/29/music-time-tracking-web-application/
categories:
  - HTML
  - javascript
  - node.js
  - Projects
  - web
tags:
  - html
  - javascript
  - node.js
  - web
---
<div>
  <p>
    I wanted to help my buddy out with some things that he wanted to do for his music class. The idea is that he wanted a site that would track his students&#8217; practice time. Simple enough.
  </p>
  
  <p>
    For this task, I used node.js with Azure as the hosting. I had to pull in a bunch of libraries:
  </p>
  
  <pre>1) <a href="https://github.com/jaredhanson/passport">login using passport</a>
2) <a href="http://www.datejs.com/">Date Time javascript library</a>
3) <a href="https://github.com/WindowsAzure/azure-sdk-for-node">Azure Table Storage</a>
4) <a href="https://github.com/andris9/Nodemailer">Node emailer</a>
</pre>
  
  <p>
    So the students just need to log in and see their time:
  </p>
  
  <p>
    <img src="http://jordenlowe.com/wp-content/uploads/2016/02/login.png" alt="login" width="300" />
  </p>
  
  <p>
    Next, the students can input their time on this screen:
  </p>
  
  <p>
    <img src="http://jordenlowe.com/wp-content/uploads/2016/02/timesheet.png" alt="login" width="300" />
  </p>
  
  <p>
    They can also see how well they are doing here:
  </p>
  
  <p>
    <img src="http://jordenlowe.com/wp-content/uploads/2016/02/history.png" alt="login" width="300" />
  </p>
  
  <p>
    The students can even email the teacher a message about the site:
  </p>
  
  <p>
    <img src="http://jordenlowe.com/wp-content/uploads/2016/02/email.png" alt="login" width="300" />
  </p>
  
  <p>
    On the teacher&#8217;s side, they log in to a different URL and see their students progress and time:
  </p>
  
  <p>
    <img src="http://jordenlowe.com/wp-content/uploads/2016/02/teacher.png" alt="login" width="300" />
  </p>
  
  <p>
    All in all, I got more familar with Node&#8217;s packages, which helps me out in the long run. The sad part about this is I did not get more exposure to an MVC framework like angular.js, but that&#8217;s for the next project :-).
  </p>
  
  <p>
    If you are interested in the site, take a look at it on git hub, <a href="https://github.com/supermitsuba/musictracker">Music Tracker</a>
  </p>
</div>