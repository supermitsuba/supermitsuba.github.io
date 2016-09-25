---
id: 61
title: How to Develop XML Documents
date: 2013-04-28T00:00:00+00:00
author: Jorden
layout: post
guid: http://www.fbombcode.com/title/How_to_Develop_XML_Documents
permalink: /2013/04/28/how-to-develop-xml-documents/
categories:
  - XML
tags:
  - XML
---
 <p> I recently had some issues with XML holding data. Lots of repeated data, and large object models caused a little bit of an issue creating these by hand. So how should you go about using XML? </p> <p> I found an interesting article on the definitions of XML document types: <a href="http://www.rpbourret.com/xml/XMLAndDatabases.htm">http://www.rpbourret.com/xml/XMLAndDatabases.htm</a>. The article pointed out 2 xml types, Data and Document. </p> <p> Data-centric xml, is more machine processed and used for transportation of data between systems. This is not generated/read by humans, like rss feeds, and instead read into other systems for processing. On the other hand, document-centric xml is processed more like html. The mark-up is described and manipulated by humans to do work. While the article goes on to describe how to integrate these types of xml documents into an xml-centric database, I got a good sense of how to describe and organize xml that was causing me grief. </p> <p> I think most of the issues I have had with XML recently is that I am looking at data-centric xml and hand editing it. If I was to do any hand-editing, I should describe something a bit looser like HTML, or build a system that generates the XML. </p> <p> <strong>\*UPDATE\* 5/9/2013</strong> </p> <p> So, at work we figured out our issue with XML. We ended up adding another layer of abstraction, so that we could specify the repeated data in a variable and we use a utility to generate the xml files for each environment. Just goes to show, sit down with everyone and you will find a solution to a shitty situation. </p>