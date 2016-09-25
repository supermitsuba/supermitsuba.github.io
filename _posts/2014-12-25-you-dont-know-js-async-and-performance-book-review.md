---
id: 16
title: 'You Dont Know JS: Async and Performance: Book Review'
date: 2014-12-25T00:00:00+00:00
author: Jorden
layout: post
guid: 'http://www.fbombcode.com/title/You_Dont_Know_JS:_Async_and_Performance:_Book_Review'
permalink: /2014/12/25/you-dont-know-js-async-and-performance-book-review/
categories:
  - javascript
  - web
tags:
  - async
  - javascript
  - web
---
 <p> I had this book for a while and finally read it. Great stuff about asynchronous programming in general. They are really tips about how to think about Async and Promises. </p> <p> The books author is Kyle Simpson. The book is about asynchronous programming in JavaScript. There are 3 chapters, &#8216;Asynchrony: Now and Later&#8217;, &#8216;Callbacks&#8217; and &#8216;Promises&#8217;. Each chapter feeds into the next and it is the story of how you can rewire your JavaScript to make more sense. </p> <h2> Asynchrony: Now and Later </h2> <p> The book starts off by breaking down what JavaScript is, and how it is one big event loop. This loop allows callbacks to queue up to be executed asynchronously. The book then compares this with parallel programming and shows how async code in JavaScript is more deterministic than what threads would be, but there are still non-determinism within JavaScript. This can lead to race conditions. The last bit of the chapter then says to keep your code simple, breaking your code into small chunks will help out. </p> <h2> Callbacks </h2> <p> Callbacks were born out of making small, reusable functions. This chapter starts talking about callbacks and some of the drawbacks they have. Issues of &#8216;callback hell&#8217;, events firing too early, or late or never. The unfortunately truth is that they make your code ugly and hard to read. This leads into Promises. </p> <h2> Promises </h2> <p> Promises help change the inversion of control in callbacks. This then makes callbacks readable, and thus code easier to maintain. The rest of the chapter goes over how awesome promises are and how they can mitigate callback hell, and solve those issues with firing too early or late. </p> <p> Ultimately, this book has helped me to think about asynchronous programming a bit differently. One, thing is to break up your data so that callbacks are fast and don&#8217;t tie up the UI thread. The other thing is how Promises are mimicked in other languages, like C#s async and Task Parallel Library. A neat book, short but good read to refresh my brain on JavaScript and asynchronous programming. </p>
