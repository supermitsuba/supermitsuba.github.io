---
id: 70
title: Fun with Node.js
date: 2013-03-10T12:00:00+00:00
author: Jorden
layout: post
guid: http://www.fbombcode.com/title/Fun_with_Node.js
permalink: /2013/03/10/fun-with-node-js/
categories:
  - javascript
  - node.js
tags:
  - javascript
  - node.js
---
 <p> Node.js is a pretty powerful server side javascript processing engine. It is so powerful that it is a surprise that it was developed in 2009. Even though it is relatively new, it has a huge following, and supports a massive community with tons of open source packages to use. If you were looking to get your feet wet with node.js or get an idea of what it is, take a peek at the article. </p> <p> I am amazed at how much you can do with node.js, so for now let�s start off with creating a simple web server. The nice thing with the web server is that there are packages out there to help with them. I am going to start off with a package called �Express�. In order to use a package, you have to �require� the package. It�s sorta like an include: </p> <figure> <code> <img src ="/img/9.png" /> </code> </figure> <p> Next, we need to add some web server settings to get the program up and running. First, I will set up the local directory to expose through the web server. Next, we will need requests and responses to be parsed automatically for us. Lastly, we need to set up some view engine options to tell express to use a template engine. In the example below I used <a href="http://embeddedjs.com/">EJS</a>. </p> <figure> <code> <img src ="/img/10.png" /> </code> </figure> <p> Now, you can start to accept web requests, here is a post: </p> <figure> <code> <img src ="/img/11.png" /> </code> </figure> <p> You will probably notice a few things. One, the post needs a url rotue. Here the route is: �/Blog/:id�. The :Id part is for a query string parameter. Now on the second parameter, there is a call back function. This gets called every time someone request the url. The last thing to note is the parameter that the ID represents: req.param.Id, is the same ID that is shown in the url routing. Now let�s check out a post: </p> <figure> <code> <img src ="/img/12.png" /> </code> </figure> <p> Here, a user is posting back to the url �MyAwesomeRestPost�. The post body variable is being parsed and placed in the request object. Then we took that value and now we are sending back to response variable. </p> <p> Super easy, right? Now I forgot, you can specify the port by this last line below. This is where the web site will be hosted. All that together will get you to host a simple website. Node.js is definitely an awesome web framework to get something quick and working. </p> <figure> <code> <img src ="/img/13.png" /> </code> </figure>