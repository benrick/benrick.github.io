---
layout: post
title: "Common Reuse Principle"
date: 2012-04-02 11:00:00 -0400
comments: true
published: true
categories: ["Archive"]
tags: ["Common Reuse Principle", "Calendar Topic"]
permalink: "/post/Common-Reuse-Principle/"
---
<!-- more -->



<p>Classes that are used together are packaged together.</p>  <p>This is the April topic from 2011 NimblePros Software Craftsmanship Calendar, which includes a nice quote.</p>  <blockquote>   <p>Common Reuse Principle (CRP):     <br />Classes should be packaged together when reusing one will mean reusing them all. Source: “Agile Principles, Patterns, and Practices in C#”      <br />by Robert C Martin</p> </blockquote>  <p>This is a pretty simple principle, and one that should seem quite logical. Not everyone agrees with the principle, but it least has a good point. If two things are going to be reused together, it makes logical sense that you should package them together. </p>  <p>Imagine if we didn’t follow this for ASP.NET and instead had everything spread around in some random assortment of assemblies. If I were accessing my HttpRequest, which is normally in the System.Web assembly and doing something with the cookies from that, which is an HttpCookieCollection. That HttpCookieCollection is a collection of HttpCookie. All of these are in System.Web, since they’re commonly used together. There is one assembly that we need to use this full set of classes.</p>  <p>Now think of how much fun this development experience would be if we had broken these apart such that the HttpRequest was in the System.Web assembly, HttpCookieCollection was in System.Web.Collections assembly, and HttpCookie was in the System.Web.State assembly. That would mean having to access three different assemblies to get three closely related classes.</p>  <p>Don’t get me wrong, I like having smaller, broken up dependencies, so that I don’t have to depend on a lot of things I don’t need. In fact, I have to have a good number of assemblies when I use the onion architecture. (They’re not all compile time dependencies everywhere they’re used though.)</p>  <p>The painful part, however, is when there are obvious pieces that should be together and aren’t. Common reuse is basically saying that there is pretty much no time that I would use HttpCookieCollection without also needing HttpCookie, so they should be in the same package. (Just those two from my example. I think that HttpRequest could be somewhere else with a good reason for it. Although we all know that all of these classes are in the same assembly right now.)</p>  <p>What’s your take on it? There is a lot of gray area with Common Reuse Principle.</p>
