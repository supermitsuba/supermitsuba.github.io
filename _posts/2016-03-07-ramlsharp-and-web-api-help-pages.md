---
id: 209
title: RamlSharp and Web API Help Pages
date: 2016-03-07T02:17:59+00:00
author: Jorden
layout: post
guid: http://jordenlowe.com/?p=209
permalink: /2016/03/07/ramlsharp-and-web-api-help-pages/
categories:
  - general
---
I have been trying to see why attribute-based routing works, and convention-based routing doesn&#8217;t work.  I had to debug a convention-based Web API to find out.  What I found out was how Web API Help Pages APIs gets routes.

The issue with convention-based routing is that it writes one record for a route template, then has multiple routes under that.  Attribute-based routing works the exact opposite.  It adds a &#8220;route template&#8221; for each route.

Instead of using the route template, I might be able to use RelativePath and look at the ParameterDescriptor instead.  This should be able to get the correct routes with parameters.  Of course I will have to test this all out, but I should be able to support convention-based routing again.