---
layout: post
title: "Time-Tested Testing Tips - Part 1"
date: 2009-05-19 10:04:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Blog"]
permalink: "/post/Time-Tested-Testing-Tips-Part-1"
---
<!-- more -->

<p>These days more and more people seem to be testing. I admit I am one of the developers who has been writing unit, integration, acceptance, regression, and other tests. The idea of testing has been around for a long time, but it seems lately there has been a surge of people beginning to use them. Some are having great success and some are seeing their success fall away. Simply <em>writing</em> tests does not suddenly make great code.</p>
<p>Something I think everyone should know is that testing code is desired because it allows us a few benefits; the confidence that everything is working, the confidence that a bug has been eliminated, ease of maintainability, and extra documentation of a system written in code.</p>
<h3>Tests as Documentation</h3>
<p>I believe I've said plenty of times in the past that the tests you write become excellent documentation which can be used to demonstrate how different aspects of your system should be used. This is very useful for someone joining a project. If it is well-documented in its tests, learning how to work with the code is as easy as reading through the tests and seeing how the different objects are intended to interact. If you can't do this, you're probably not testing well.</p>
<p><strong>A good measure of your application's testing is to have someone learn to use the system based solely on the tests. If the tests are written well enough, someone will be able to figure out how everything works and interacts.</strong></p>
<p>This is one of my primary goals when testing an application. I want to make sure that things are clear, because when I come back to this code a month from now I will be that new developer on the project. I will need to know how to use the classes, interfaces, etc. and having it documented in working cases goes a long way.</p>
<h3>How many tests should I write?</h3>
<p>This is one of the most common questions asked by new testers. For now I will take the cowardly approach and say, "it depends". I've read posts from people touting the number of tests they've written. This is a new metric as if "line count" wasn't already bad enough. There is a balance here that we are looking for. Just with the line count.</p>
<p>If your line count is small you're application probably doesn't do very much and if it is large then your application might be cumbersome and difficult to maintain. When you don't have many tests your code is more prone to errors, but if you've written too many tests maintainability disappears. But wait! Didn't I say earlier that tests make code <em>more</em> maintainable. Well, yes I did, but if you write too many it becomes difficult to change the code. If you test every single possible minute little thing in your application you're going to have a heck of a time changing anything.</p>
<p><strong>When you're writing tests make sure you have <em>just enough</em> to give yourself confidence that your code is working. </strong></p>
<p>I highly recommend against ever setting code coverage or test count goals. If you set goals for these you're just creating incentives to write more tests than is required. Too many tests can create the same problems as too much code. Why? Because tests <em>are</em> code.</p>
<p>You need to <a href="http://brendan.enrick.com/post/2009/02/26/Treat-Your-Tests-Well.aspx" target="_blank">treat your test code well</a>. It needs to follow a lot of the same rules as the rest of what you write.</p>
