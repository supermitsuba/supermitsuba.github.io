---
id: 26
title: Building Generic HAL Browser
date: 2014-08-24T00:00:00+00:00
author: Jorden
layout: post
guid: http://www.fbombcode.com/title/Building_Generic_HAL_Browser
permalink: /2014/08/24/building-generic-hal-browser/
categories:
  - .net
  - web
tags:
  - .net
  - REST
  - Restful API
  - web
---
 <p> At work, I wanted to browse our Hypermedia API, but also wanted to play with how we could generate a generic HAL browser. It wasn&#8217;t too crazy but here is some of the things I found. </p> <p> The biggest problem with Hypermedia API&#8217;s is the tooling. Now, you could just use a REST client, but that may not help you be able to build something in your language of choice. Mine happens to be C#. I have seen some of the HAL libraries out there for C#, but they weren&#8217;t that great. That may have changed, but I wanted to go about making one myself. </p> <p> The biggest thing I discovered is that dictionaries are one of the only ways to encapsulate the logic that you may want. Here is what I created for a HAL response: </p> <pre class="formatCode"> public class HalObject { public HalObject(IDictionary<string, string> dataProperties, IDictionary<string, IList<halObject>> embeddedResources, IDictionary<string, IList<link>> links) { DataProperties = dataProperties; EmbeddedResources = embeddedResources; Links = links; } public IDictionary<string, string> DataProperties { get; private set; } public IDictionary<string, IList<halObject>> EmbeddedResources { get; private set; } public IDictionary<string, IList<link>> Links { get; private set; } } </pre> <p> A HAL response is pretty standard, a section for your data, a set of embedded resources and a list of links. </p> <p> Once I got it going, I used my api at <a href="/api">/api</a>, and was able to get feedback from dog fooding that. Next, I&#8217;ll be going to work to see how well it plays there. If you want to use the browser, you can get it from my git repo at: <a href="http://github.com/supermitsuba/GenericHalBrowser">http://github.com/supermitsuba/GenericHalBrowser</a> </p> <p> I&#8217;ll probably build some more tooling around it, as it can only handle GET requests, and no options for templated query string parameters. If you have suggestions, questions or comments, please feel free to add a comment. </p>