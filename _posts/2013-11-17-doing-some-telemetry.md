---
id: 41
title: Doing some telemetry
date: 2013-11-17T00:00:00+00:00
author: Jorden
layout: post
guid: http://www.fbombcode.com/title/Doing_some_telemetry
permalink: /2013/11/17/doing-some-telemetry/
categories:
  - general
---
 <p> At work I have been working on collecting information from our new web api project that we are working on. We have had a few things that we track, but thought I would throw an article out here to see if anyone else has suggestions. </p> <p> So we collect this information from our apps right now: </p> <div> <ol> <li>1)Collect time of a function call or stack call</li> <li>2)How many times we are calling a feature</li> <li>3).Net version of the client app</li> <li>4)What version of the telemetry client we are using.</li> <li>5)All the apps that use the api.</li> <li>6)Memory and CPU usage.</li> </ol> </div> <p> All this information gets packaged up, async, and sent to a message queue. We then use a service to process all the messages. Do you guys think I should collect anything else? </p>