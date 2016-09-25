---
id: 65
title: How to use Signal R
date: 2013-03-28T00:00:00+00:00
author: Jorden
layout: post
guid: http://www.fbombcode.com/title/How_to_use_Signal_R
permalink: /2013/03/28/how-to-use-signal-r/
categories:
  - .net
  - asp.net
  - javascript
  - web
tags:
  - .net
  - c
  - javascript
  - signal r
  - web
  - web sockets
---
 <p> So I played with <a href="http://signalr.net/">SignalR</a> a long while ago in one of it&#8217;s beta phases. I came back to it and found it completely different. With this post, I plan to talk about SignalR 1.0.1 and how to use it. 🙂 </p> <p> So SignalR creates a QUICK F**KING Pub Sub with ease. Now most people I have talked to have said it scales like crap and is not ready for primetime enterprise just yet, but I do find it valuable for smaller use cases. So let&#8217;s start off with some things to do first with Signal R: </p> <pre class="formatCode"> protected void Application_Start() { AreaRegistration.RegisterAllAreas(); RouteTable.Routes.MapHubs(); WebApiConfig.Register(GlobalConfiguration.Configuration); FilterConfig.RegisterGlobalFilters(GlobalFilters.Filters); RouteConfig.RegisterRoutes(RouteTable.Routes); BundleConfig.RegisterBundles(BundleTable.Bundles); } </pre> <p> So basically start off by creating an MVC 4 app, and head to the global.asmx. There, you will want to add the RouteTable in line 2. This says that you want to route Hubs, but you might ask where? Well we will find out where later, but next let&#8217;s create a new folder called SignalR off the root of the project. Not in the Views or Controllers, just the root. </p> <p> Once that folder is created, create a class and inherit Hub, like below: </p> <pre class="formatCode"> using System; using System.Collections.Generic; using System.Linq; using System.Web; using Microsoft.AspNet.SignalR; namespace BLT.SignalR { public class BaconJob : Hub { public const string key = "Server:{0}Job:{1}"; public void Distribute(string server, string job, string message) { Clients.Group(string.Format(key, server, job)).receive(message); } public void Join(string server, string job) { Groups.Add(Context.ConnectionId, string.Format(key, server, job)); } } } </pre> <p> This code is creating 2 server calls for SignalR, Distribute and Join. Join will add a client to a topic, like a subscription. Distribute method will cause a message to distribute to all the clients associated with the key. </p> <p> Next, let&#8217;s add this javascript to our page: </p> <pre class="formatCode"> </pre> <p> And add this HTML: </p> <pre class="formatCode"> <section class="featured"> <div class="content-wrapper"> <div id="content"></div> <div> <input type="button" id="sendMessage" value="Send Message" /> </div> </div> </section> </pre> <p> So that route you created before in the global.asmx; this allows the SignalR javascript to find the hubs and communicate. In the previous version of SignalR there was no &#8220;server&#8221; property and all the objects were dynamic. So, despite all the changes, it works the same&#8230;.Yay!!!! Have fun. <p>