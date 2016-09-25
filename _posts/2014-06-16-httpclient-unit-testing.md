---
id: 29
title: HttpClient Unit Testing
date: 2014-06-16T00:00:00+00:00
author: Jorden
layout: post
guid: http://www.fbombcode.com/title/HttpClient_Unit_Testing
permalink: /2014/06/16/httpclient-unit-testing/
categories:
  - .net
  - unit testing
tags:
  - .net
  - async
  - unit testing
---
 <p> Looking to mock out your favorite HttpClient API in .net. Well here is one way to go about it. </p> <p> So if you want to mock out HttpClient, remember what the client was built on, a chain of responsibility pattern. </p> <pre class="formatCode"> public class HttpClient : HttpMessageInvoker { public HttpClient(); public HttpClient(HttpMessageHandler handler); public HttpClient(HttpMessageHandler handler, bool disposeHandler); } </pre> <p> HttpClient has a constructor that takes an HttpMessageHandler. What you could do instead is create an HttpMessageHandler to intercept a message being sent and insert your code own code into it. Example: </p> <pre class="formatCode"> class MockMessageHandler : HttpMessageHandler { public Func<httpRequestMessage, System.Threading.CancellationToken, Task<httpResponseMessage>> funcToOverride { get; private set; } private MockHttpMessageHandler() { } public MockHttpMessageHandler(Func<httpResponseMessage> sendFunc) { funcToOverride = (httpRequestMessage, cancellationToken) => { return Task<httpResponseMessage>.Factory.StartNew(sendFunc); }; } protected override Task<httpResponseMessage> SendAsync(HttpRequestMessage request, System.Threading.CancellationToken cancellationToken) { return funcToOverride.Invoke(request, cancellationToken); } } </pre> <p> So above, what you would do is pass in a Func that returns an HttpResponseMessage. This is like in Moq, where you would set up a function through setup. Now you can return a Mock HttpResponseMessage or exception, whatever you are trying to test in your code. Let&#8217;s see an example: </p> <pre class="formatCode"> MockHttpMessageHandler helper = new MockHttpMessageHandler( () => new HttpResponseMessage(System.Net.HttpStatusCode.OK) { Content = new StringContent(JsonConvert.SerializeObject(document)) } ); MockHttpMessageHandler actual; using (HttpClient client = new HttpClient(helper)) { actual = client.GetAsync("/whatever"); } Assert.IsEqual(/\*your expected response message\*/, actual); </pre> <p> This now allows you to short circuit the client from calling out to a web service and return data that you would expect in your api. </p>