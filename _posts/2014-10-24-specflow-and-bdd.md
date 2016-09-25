---
id: 22
title: SpecFlow and BDD
date: 2014-10-24T00:00:00+00:00
author: Jorden
layout: post
guid: http://www.fbombcode.com/title/SpecFlow_and_BDD
permalink: /2014/10/24/specflow-and-bdd/
categories:
  - .net
  - unit testing
tags:
  - .net
  - bdd
  - spec flow
  - unit testing
---
 <p> For a while, we have been building apps that use unit testing and integration testing. While these testing approaches have really helped improve the quality of applications upon release, there are other approaches out there as well. At work, people have talked about BDD a bit and in .net there is a framework called SpecFlow. Here is how I set it up. </p> <p> First off, you can go to the site here at: <a href="http://www.specflow.org/getting-started/">http://www.specflow.org/getting-started/</a>. The steps to set up a project are easy: </p> <ol> <li>1. In Visual Studio, download the SpecFlow Plugin.</li> <li>2. Create a MSTest project. (side note, if you want to do NUnit, just follow the linked tutorial)</li> <li>3. In the MSTest project, include the SpecFlow nuget project.</li> <li>4. Now you can create a Feature file.</li> <li>5. After creating a feature, Generate the test code stubs from the Feature file.</li> <li>6. The stubs are for you to implement with code.</li> </ol> <p> Now, compare those steps with the tutorial, and I think you will find that it is easy to setup SpecFlow. One of the issues I am running into is how to write SpecFlow tests. They seem like integration tests, but the specs are written by QA/Business. If this is the case, how do we make sure we reuse the DSL features. This may be something others at work will find out. </p> <p> If you have any experiences with SpecFlow, please let me know. Thanks! </p>