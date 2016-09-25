---
id: 187
title: The old blog site
date: 2013-07-14T15:58:11+00:00
author: Jorden
layout: post
guid: http://jordenlowe.com/?p=187
permalink: /2013/07/14/the-old-blog-site/
categories:
  - any
  - HTML
  - javascript
  - node.js
  - Projects
  - web
tags:
  - javascript
  - node.js
  - REST
  - web
---
<div>
  <p>
    This is one of my first sites that I have hosted myself. There were so many different things that I had to do for this project, so it was a bit of a learning experience for me. Here are the things I learned from implementing the site:
  </p>
  
  <pre>1)Figure out hosting
2)Develop or Use a blog engine
	2a)In developing, I learned about HTML5 and &lt;a href="/blog/5"&gt;Templating&lt;/a&gt;
	2b)Javascript and using libraries like &lt;a href="/blog/9"&gt;Linq&lt;/a&gt;
	2c)CSS3, &lt;a href="/blog/6"&gt;Responsive UI&lt;/a&gt;, &lt;a href="/blog/7"&gt;Google Prettyify&lt;/a&gt;
	2d)Picking a server technology (&lt;a href="/blog/3"&gt;node.js&lt;/a&gt;)
	2e)Picking MySQL database
3)Optimize site for performance
</pre>
  
  <p>
    I discussed why I wanted to build a blog <a href="http://jordenlowe.com/2013/02/10/why-would-you-want-to-write-a-blog/">here</a>, but with this project, I also wanted to learn HTML5, CSS and Javascript by diving deep into it. Building my own site would give me great insight into this technology, so I had to start with hosting. I received a free account with <a href="http://www.windowsazure.com/en-us/">Microsoft Azure</a> for having an MSDN account through Quicken, so I decided let&#8217;s try this platform out. The great thing about Azure is there are multiple different options to host, and it was great to see them.
  </p>
  
  <p>
    I started with a VM. It worked great, but the idea of maintaining it was something I did not want to do. The VM&#8217;s come in Linux and Windows flavors, so if you are looking to use them, go for it. The real lesson learned was Microsoft Azure does not have to be just Microsoft products.
  </p>
  
  <p>
    Next, I looked into web workers and web sites. The thing I took away from these 2 options is that they will allow you to not maintain a system, which is great. Web workers give you more control of administrative tasks that need more access, at the cost of process time per hour. Web sites, do not have need for administrative tasks, and are cheaper, so I decided to select the websites.
  </p>
  
  <p>
    After selecting all of this, I needed a blog engine. Like I said above, I wanted to build something to learn more about administrating a site. This meant that I didn&#8217;t want to go for the obvious selection of blogger or a word press site. Now it is true I am a .Net developer, I decided I needed MORE hands on experience with Javascript, which made me select node.js as the technology choice for the engine.
  </p>
  
  <p>
    I threw together all the stuff from section 2a-e and made great progress with the site. It worked great, but one of the things I did notice, once the initial site was up, was that I needed to worry about too many connections to the database. With <a href="http://www.cleardb.com/">ClearDB</a>, which is the provider of MySQL for Azure, you only have a few connections. Makes me wish I had a DBA team dedicated to my project like at work, but it was a good lesson about conserving resources. So in order to help with connections, I put a pool in place to help manage connections properly. Of course, with limited connections, the site responses slow with more users, as they are waiting for connections to free up. There is a solution for this, Caching.
  </p>
  
  <p>
    I built a caching library that expired old data based on time and number of caching objects. The library was easy to build out using the linq library, as I could find old data easy to eliminate stale data properly. All of this, put together, is what is keeping the site from hitting the database. As time goes on, I may need to switch to redis if I add more and more server instances, but my single server caching will do for now. The point is, this project has been great for learning how to host, maintain and use a great platform. Of course, if you have any questions about how I implemented this, please let me know at <a href="mailto:jordenashleylowe@gmail.com">jordenashleylowe@gmail.com</a>
  </p>
</div>