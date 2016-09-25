---
id: 46
title: What is REST
date: 2013-09-13T00:00:00+00:00
author: Jorden
layout: post
guid: http://www.fbombcode.com/title/What_is_REST
permalink: /2013/09/13/what-is-rest/
categories:
  - web
tags:
  - REST
  - Restful API
  - web
---
 <p> If you came here to see about sleep, then you have come to the wrong page. If you came here to talk about using HTTP as your communication pattern, then you come to the right place. Although, partially true REST uses HTTP to do it&#8217;s communication, what else do we miss if we are just talking about a &#8220;restful API&#8221;? </p> <p> When I first started to do &#8220;Restful API&#8217;s&#8221;, I thought it was just making the URI pretty for clients. Then, I started getting into HTTP and all the things that come with that, like the verbs, status codes, headers, etc. But now, I have found, that I am missing ONE MORE PIECE. That piece is super simple: the web. What are you talking about Jorden? Too much beers again? Maybe, but take a step back and look at how you use the web. I visit a URL, click links to other &#8220;resources&#8221;, read some more and so on. This is what makes the web flexible, awesome and scalible. But let&#8217;s put some perspective on this. </p> <p> Say you have an API, an order system. You want to find something programmatically. You would visit your url, http://derp.com/orders/1234. Nice, now you wanted to see who made that order, but all this url returned was this: </p> <pre class="formatCode"> { '1234':{ 'description':'derpball', 'price':'2.00', 'quantity':'1', 'user':'http://derp.com/user/1' } } </pre> <p> So, we have only sent a small amount of data. This is good because we are not wasting resources sending you all the resources that are linked to this order. Instead we are sending you more links, just incase you want to &#8216;visit&#8217; those sites for that information. The beauty of this is for scaling out the &#8216;user&#8217; resource, if needed, and to limit the amount of data coming back. THIS IS REST. Not only rest, but what hypermedia API&#8217;s are all about. Because of the URL, you are utilizing HTTP GET verb, which you can put some caching on that. if a particular resource is getting used a lot, you can scale out that resource, without the other resources being affected. And you get only the data you want. Give it a thought and try it out. </p>