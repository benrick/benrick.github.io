---
layout: post
title: "Writing Clean Code is a Process"
date: 2009-06-02 15:02:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Blog"]
alias: ["/post/Writing-Clean-Code-is-a-Process", "/post/writing-clean-code-is-a-process"]
---
<!-- more -->

<p>I was copied on an email recently from someone reluctant to begin writing unit tests for code. One of the complaints about the idea of starting late game adding in testing was an interesting one. The person mentioned that because they're starting to test so late that they will not get "all the benefits of TDD". Well, that person is correct. However, that should not stop anyone from making things <em>better</em>.</p>
<p>Recently the "boy scout rule" was brought up to me in the context of coding, and I admit I'd never thought of how well that example applies. The scouts have a rule to leave a camp site cleaner than they found it. This is a great idea since it means that gradually overtime you will be making <em>improvements</em>. No one is saying to go and spend a month cleaning things. That would be a <em>HUGE</em> waste of developer effort from the customer's perspective.</p>
<p>A good rule to live by and one I try to practice regularly is to refactor and clean a little bit every time you touch a file. Even if this just means adding a test or even renaming a bad class, interface, or variable name, the important thing is to make these minor improvements every time you get into some piece of code.</p>
<p>Another complaint about switching was that developers would be spending 50% of their time writing tests. Well I will say that that isn't quite right, but the idea there is accurate. The amount of code written is about half test code and half production code. The advantage of having the tests is less time spent debugging and fixing. Most developers have heard about the cost to fix bugs at different points during the development lifecycle, but I will summarize it as, "the sooner you catch a bug the cheaper it is to fix". If we have tests in place we find the bug sooner. This means the end cost is less, so writing the tests should <em>save</em> us money during development as well as during maintenance.</p>
<p>I admit when I first got introduced to testing I thought a lot of the same stuff. I figured the tests would slow down the development and wouldn't help very much. I figured there would be all these issues, and I'll also admit that it is pretty tough to start doing. Once you start writing tests for things you start to see some of the benefits. The best thing to see is when you change some piece of code and something seemingly unrelated has a test break. That is when you realize the connection and prevent a bug from being created. That is one of the best aspects of testing.</p>
