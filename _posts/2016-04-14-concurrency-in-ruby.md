---
id: 222
title: Concurrency in Ruby
date: 2016-04-14T03:39:17+00:00
author: Jorden
layout: post
guid: http://jordenlowe.com/?p=222
permalink: /2016/04/14/concurrency-in-ruby/
categories:
  - ruby
  - web
tags:
  - concurrency
  - concurrent-ruby
  - ruby
  - web api
---
When first reading about ruby, the first thing that made me worried was I/O bound processes.  Lot of people bashed ruby for the GIL (global interpreter lock) and said that it made ruby slow.  But if you look at the [ruby-concurrent](https://github.com/ruby-concurrency/concurrent-ruby) library, it looks as though ruby can handle asynchronous transactions.  It has support going back to [ruby 1.9.3](https://www.ruby-lang.org/en/news/2011/10/31/ruby-1-9-3-p0-is-released/), which was release in 2011.

So to test it myself, I decided to write some code to see how it worked.  First I created a quick node.js server to give me a web call to test.  In the server, I added random timeouts for a response, ranging from 500 ms to 3 seconds.  This would allow me to see if I made, say 11 requests at once, that I should see those requests return in order of the smallest random timeout to the largest.  Here is the code I wrote:

<pre class="lang:default decode:true" title="Web Service Code">var express = require('express');
var app = express();

app.get('/api/test/:id', function (req, res) {
  var time = randomIntFromInterval(500, 3000);
  var currentTime = Math.floor(new Date() / 1000);
  var id = req.param('id');

  console.log(currentTime + " @ Waiting for : "+ time + " seconds. ID " + id);
  this.setTimeout(function() {
    res.send('Hello World!');
  }, time);
});

app.listen(3500, function () {
  console.log('Example app listening on port 3500!');
});

function randomIntFromInterval(min,max)
{
    return Math.floor(Math.random()*(max-min+1)+min);
}
</pre>

Next, I used ruby-concurrent to make 11 web calls at a time asynchronously.  After the 11 calls, I would call sleep for 3 seconds.  Here is that code:

<pre class="lang:default decode:true " title="Ruby Concurrent Code">require 'concurrent'
require 'rest-client'

class ThreadTest
  include Concurrent::Async

  def WebCall(number)
    puts "Started #{number}"
    RestClient.get "http://localhost:3500/api/test/#{number}"
    puts "Completed #{number}"
  end

end

i = 0
while true do
  test = ThreadTest.new
  test.async.WebCall i

  if i % 11 == 0
    sleep(3)
  end

  i = i + 1
end</pre>

What I saw was that ruby would make the 11 calls, but print them out of order.  But that is fine because when you make 11 async calls, you would expect them to be thrown on a queue and processed slightly out of order because of how async can work.  Here is the output of the ruby code:

<pre class="lang:default decode:true">Started 2
Started 1
Started 3
Started 4
Started 5
Started 6
Started 7
Started 8
Started 9
Started 11
Started 10
Completed 8
Completed 10
Completed 11
Completed 9
Completed 6
Completed 7
Completed 1
Completed 2
Completed 3
Completed 5
Completed 4</pre>

Now, what I imagine would happen is that the completed order on the client would match the server random times, which is exactly what happened:

<pre class="lang:default decode:true">1460602540 @ Waiting for : 1774 seconds. ID 1
1460602540 @ Waiting for : 2193 seconds. ID 2
1460602540 @ Waiting for : 1392 seconds. ID 11
1460602540 @ Waiting for : 1442 seconds. ID 9
1460602540 @ Waiting for : 1518 seconds. ID 6
1460602540 @ Waiting for : 1234 seconds. ID 8
1460602540 @ Waiting for : 1700 seconds. ID 7
1460602540 @ Waiting for : 1378 seconds. ID 10
1460602540 @ Waiting for : 2562 seconds. ID 5
1460602540 @ Waiting for : 2336 seconds. ID 3
1460602540 @ Waiting for : 2858 seconds. ID 4</pre>

You can see that 8 had the shortest response time, and so it finished first, followed by 10 and 11 and so on.  This is cool cause this validates that ruby is keeping up with what features other languages are using in their frameworks, too.  Not just Node, C#, or even Erlang are asynchronous, but so is ruby.  Now, why it is slow may be other issues, like the package sprawl that is in ruby on rails, but that is another issue I will be looking into to see how we can get the best performance out of our platform.