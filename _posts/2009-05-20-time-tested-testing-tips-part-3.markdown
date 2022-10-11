---
layout: post
title: "Time-Tested Testing Tips - Part 3"
date: 2009-05-20 09:23:00 -0400
comments: true
published: true
categories: ["Archive"]
tags: ["TDD", "Unit Testing", "Tips"]
permalink: "/post/Time-Tested-Testing-Tips-Part-3/"
---

<p>Context switching is very costly and this same issue can be seen when writing tests, but I would argue most importantly in maintaining and reading tests.</p>
<ul>
<li><a href="/post/Time-Tested-Testing-Tips-Part-1.aspx" target="_blank">Time-Tested Testing Tips - Part 1</a></li>
<li><a href="/post/Time-Tested-Testing-Tips-Part-2.aspx" target="_blank">Time-Tested Testing Tips - Part 2</a></li>
</ul>
<p>There are three main parts to a test. The first part sets everything up, the second part takes some action, and the third part expects certain results given the the start and the action taken. In this tip I'll be talking about the first part, the setup.</p>
<h3>Keep Test-Relevant Details Visible</h3>
<p>I've said in the past to treat test code just like any other code. However, there are a few reasons to break from this rule. One is the context switching which will be caused by extracting information which is important to a test. Let me explain what I mean with two examples.</p>
<p><span style="text-decoration: underline;">Example Using Helper Method</span></p>
<div>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; line-height: 12pt; background-color: #f4f4f4; width: 100%; font-family: consolas,'Courier New',courier,monospace; color: black; font-size: 8pt;">[Test]
<span style="color: #0000ff;">public</span> <span style="color: #0000ff;">void</span> CalcInterestRoundsToTenthPennies()
{
    <span style="color: #0000ff;">decimal</span> initialMoney = 100.00;
    <span style="color: #0000ff;">decimal</span> expectedInterest = 33.333
    InterestCalculator ic = GetTestInterestCalculator();
    
    <span style="color: #0000ff;">decimal</span> actualInterest = ic.CalcInterest(initialMoney);
    
    Assert.AreEqual(expectedInterest, actualInterest, 
      <span style="color: #006080;">"CalcInterest did not round to a tenth of a penny correctly"</span>);
}</pre>
</div>
<p><span style="text-decoration: underline;">Example Without Helper Method</span></p>
<div>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; line-height: 12pt; background-color: #f4f4f4; width: 100%; font-family: consolas,'Courier New',courier,monospace; color: black; font-size: 8pt;">[Test]
<span style="color: #0000ff;">public</span> <span style="color: #0000ff;">void</span> CalcInterestRoundsToTenthPennies()
{
    <span style="color: #0000ff;">decimal</span> initialMoney = 100.00;
    <span style="color: #0000ff;">decimal</span> interestRate = 0.3333333333;
    <span style="color: #0000ff;">decimal</span> expectedInterest = 33.333
    InterestCalculator ic = <span style="color: #0000ff;">new</span> InterestCalculator(interestRate);
    
    <span style="color: #0000ff;">decimal</span> actualInterest = ic.CalcInterest(initialMoney);
    
    Assert.AreEqual(expectedInterest, actualInterest, 
      <span style="color: #006080;">"CalcInterest did not round to a tenth of a penny correctly"</span>);
}</pre>
</div>
<p>Notice here that you can tell a lot more about what is going on in the second one, because you know what percentage is being used to calculate. You cannot tell that the first one is accurate since you can't see the percent. I recommend trying to keep the amount of values to a minimum and if you're writing your code well you'll have few enough dependencies that you will not have a problem. These helper methods as you can see make it so you will need to go to another location to see what was initially created. In some instances they are useful, but use them sparingly as they might hide away details.</p>
<h3>Do Not Unit Test Third Party Frameworks</h3>
<p>Make sure that what you're testing is part of your code and not someone else's. If you're testing code you have no access to you better not be keeping that around as an automated test. You're wasting your time if you're creating automated tests for this code. If you find a bug in the code you can tell someone about it, but you probably can't fix the code. If it is an open source project you're testing then go test the code in <em>their</em> test library and fix issues you find. You will be doing them and yourself a favor. Don't clutter your own test library.</p>
<h3>Write Automated Tests Whenever You Are Curious</h3>
<p>If I ever wonder how some piece of code or a class works or something, I could go write a simple application and test something out. I certainly do not waste my time though. It tends to be much faster just to write a test to answer my question or learn something new. If I want to try something out I just write a test. If it is an internal piece of code I go look at the existing tests, and if it is not I write a temporary one just to try something out.</p>
<p>Unit tests are quite useful for this sort of thing, and since I have keyboard shortcuts mapped to run them they're very fast. If you really want to test a lot, you need to start using them all the time. They become very easy to come up with and write once you practice them enough.</p>
