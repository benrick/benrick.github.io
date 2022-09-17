---
layout: post
title: "Time-Tested Testing Tips - Part 4"
date: 2009-05-21 22:20:00 -0400
comments: true
published: true
categories: ["blog", "Archive"]
tags: ["Blog"]
permalink: "/post/Time-Tested-Testing-Tips-Part-4/"
---
<!-- more -->



<p>Rather than spending the time with needless introduction, I think I&rsquo;ll just jump right in today. I&rsquo;ve got a few tips I am going to post today.</p>
<h3>Reproduce Bugs Using Unit Tests</h3>
<p>Yes, this is another test driven development method. When you&rsquo;re looking for a bug, it is very common to try to reproduce it. What you might try to do instead of doing this is reproduce the bug manually, fix the bug, and then write a test to prevent it. Well I think that is a pretty bad way of doing things. Reason number one is DRY; don&rsquo;t repeat yourself. Why did you reproduce it once manually and once automatically? I also wonder how you know you&rsquo;ve written the test correctly. If it never failed you can&rsquo;t be certain you&rsquo;re testing the bug.</p>
<p>If you write this test first you jump right to finding the bug. <em>Seeing the red of the test failing tells you that you&rsquo;ve found the bug</em>. Having this test will also let you run the buggy code multiple times, which can be useful if you can&rsquo;t tell right away what is causing the issue. This becomes a faster, easier process. Since you managed to get the failing test, you know that once you&rsquo;ve fixed it that you&rsquo;ve at least fixed the bug you tested. Going the other route you were left to assume that you fixed the bug. We all know what happens when we assume&hellip; Yes, that is correct, we are sometimes not accurate.</p>
<h3>Keep Dependencies to a Minimum</h3>
<p>Yes, this is another situation where we are thinking about both the test code and the production code. If you&rsquo;re finding that the objects you&rsquo;re testing are requiring a lot of set up you probably need to simplify things. Get some of these tests in place first. These will help you to clamp down the behavior you want to maintain while you <em>refactor</em>. You&rsquo;ll want to observe plenty of principles while doing this especially the single responsibility principle.</p>
<p>For example if you have a method which takes in a parameter called <em>BankAccount</em>, but all it really needed was the <em>AccountNumber</em> you should alter your method so it takes the <em>AccountNumber</em> instead. This will make testing easier and it will also lessen your dependence. These are great things to do.</p>
<p>Do not pass an object used to get another. Pass only what is required for something to achieve what it needs to. You need to keep things minimal in this sense. It will make testing as well as maintenance much easier.</p>
<h3>Make Things Work Before Making Them Right</h3>
<p>It is difficult for a lot of us to follow this, because we know so well how bad some types of code are. We try to avoid having ugly code by spending lots of time and effort trying to get things right the first time. Then we aren&rsquo;t even sure they work.</p>
<p>Plenty of times in the past, I&rsquo;ve had programming partners who wanted me to write my code better than I did the first time. Sometimes I made the foolish mistake of listening to them. If you&rsquo;re dealing with some complicated logic you need to write it the ugliest easiest way you can. This will let you get your tests passing. Once your tests are passing you are <em>free!</em> By knowing that the test and the code are working you have freed yourself up to refactor. You don&rsquo;t have to think quite so hard since you have this safety net in place. Try something. If it does not work, just revert back and try something else. You will quickly find a design that you like and keeps those tests passing.</p>
<p>Sometimes just seeing the working code will lead you to seeing a better design for it. This situation is much better than if you had spent a lot of time coming up with some way of designing it. The design might not even have worked the first time, and then you would <em>really</em> be wasting time.</p>
<p>I hope you&rsquo;ve enjoyed these tips. Remember that testing takes a lot of practice. You&rsquo;ll never see any benefits from testing if you don&rsquo;t keep writing tests.</p>
