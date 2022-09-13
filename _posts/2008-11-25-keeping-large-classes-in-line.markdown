---
layout: post
title: "Keeping Large Classes in Line"
date: 2008-11-25 22:52:00 -0500
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Blog"]
alias: ["/post/Keeping-Large-Classes-in-Line", "/post/keeping-large-classes-in-line"]
---
<!-- more -->

<p>One thing that seems to get out of control quickly on a lot of projects I've seen is a tendency for classes to grow to enormous size. This is one problem that seems to turn up at least once in a lot of projects. Why does it happen? Because programmers are lazy. Yes, I said it. We are. I think it is a good thing in a lot of cases. We are "efficiency experts". We pay an up-front cost writing a program so we will have less work to do to solve a problem. By writing the code we save ourselves time. This is one example of this laziness.</p>
<p>When we get lazy we tend to group things together. Since the foo class already has access to types x, y, and z, we can just put this new code in foo. It makes sense, but we're really just making our classes larger. This is why the single responsibility principle is so important. This is one rule important enough that developers everywhere should know about it.</p>
<p>Classes should do one, and only one, task. That is their responsibility. If you need to generate some value, write a class to do that. Don't reuse an existing class. I've seen classes which have gotten so large people don't even know what is in them. I would be scared to make modifications to files like that.</p>
<p>Keep your classes small. It is easier to test individual parts. This is why unit tests are called "unit tests". They test a small piece of the code. If you keep classes small and separate responsibilities among classes it is easier to test. You can break dependencies on the other classes using interfaces, abstract classes, or other things.</p>
<p><strong>Private Methods to discourage use</strong></p>
<p>Sometimes there are methods kept private in a class. Some calculations are kept private because nothing should be calling those methods on this class. This is a good hint that the method belongs somewhere else. If the method is kept private because it doesn't make sense for a user of this class to use it, it belongs somewhere else.</p>
<h3>Breaking Classes Apart</h3>
<p>The best way to cut large classes down to size is to go through and find pieces which don't belong and are grouped together. Often looking for the collapsible regions of code helps. If you've grouped methods into a region there is a good chance those are related methods and probably belong in a different class.</p>
<p>When you create the new class where you will put these methods, the first thing you should do is test it. This new piece should be very testable since you're pulling it out of the beast. If you test this one piece you'll be able to keep things stable while you pull apart the large class. If you aren't testing each part as you break things up, there is a very good chance you will create bugs in the process.</p>
<p>In my opinion, tests serve two very important purposes. They test to make sure that things work as expected, and they help keep code stable. This stability clamps things down and allows changes to be made. Often times after breaking off separate pieces many refactorings which were hard to find in the large cluttered class become quite obvious. This is why it is so very important to break apart large classes.</p>
