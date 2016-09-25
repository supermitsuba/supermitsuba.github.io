---
id: 20
title: 'Nedb the Node embedded database'
date: 2014-11-29T00:00:00+00:00
author: Jorden
layout: post
guid: http://www.fbombcode.com/title/Nedb_-_Node_embedded_database
permalink: /2014/11/29/nedb-node-embedded-database/
categories:
  - javascript
  - node.js
tags:
  - embedded database
  - javascript
  - node.js
---
 <p> I was writing an HTML 5 app that was going to save notes. At first I was going to use just localStorage, which is a way to save data in the browser. After using the app, I wanted something that would sync with all my devices. While I only need one server app for this, I didn&#8217;t want to use a full blown database for a small app. Thats where Nedb comes into play. </p> <p> I found NEDB when I was looking for SQLite. Although I could have used SQLite, the interfaces for it in node kinda sucked. That&#8217;s when I found NEDB and it&#8217;s github page: <a href="https://github.com/louischatriot/nedb">https://github.com/louischatriot/nedb</a>. Unlike SQLite, it works more like a NoSQL database. You can make it an in-memory database, or you can use it by saving a file. Now, because the way it saves data, append-to database, you must compact the database every once in a while for maintenance. Other than that, the database works great. Here is some examples: </p> <pre class="formatCode"> var Datastore = require('nedb') , db = new Datastore({ filename: 'path/to/datafile', autoload: true }); /\* INSERT \*/ db.insert({ my:'obj'}}, function (err, newDoc) { // Callback is optional // newDoc is the newly inserted document, including its _id }); /\* SELECT/SEARCHING \*/ db.find({ system: 'solar' }, function (err, docs) { // this searches all the objects for a property called 'solar' }); /\* UPDATING \*/ db.update({ planet: 'Jupiter' }, { planet: 'Pluton'}, {}, function (err, numReplaced) { // This searchings for a planet 'Jupiter' and replaces it COMPLETELY }); /\* DELETING \*/ db.remove({ system: 'solar' }, { multi: true }, function (err, numRemoved) { // All planets from the solar system were removed }); </pre> <p> So these are just examples from the github page. As you can see these queries are very simple and there are other options that you can look into as you need them. Some of the other options are paging, sorting and projects. All in all a very easy to use database if you are looking for something super quick. Also, the database can run in the browser too: <a href="https://github.com/louischatriot/nedb#browser-version">https://github.com/louischatriot/nedb#browser-version</a>. </p>
