---
layout: post
title: "Assumption Driven Coding"
date: 2014-06-18 10:00:00 -0400
comments: true
published: true
categories: ["blog", "Archive"]
tags: ["Calendar Topic", "Software Craftsmanship"]
permalink: "/post/Assumption-Driven-Coding/"
---
<!-- more -->



<p>As software developers, we have to make a lot of assumptions about things. It goes with the territory, however, we try to avoid making assumptions whenever we can. One of the values that we hold up is <a href="http://deviq.com/communication" target="_blank">Communication</a>, and that means that we need to communicate with our users. June 2014 is Assumption Driven Coding month according to the 2014 Software Craftsmanship Calendar Anti-Patterns edition.</p>  <p>The calendar (as always) takes a more visual approach to this software development issue.</p>  <p><a href="/images/files/Assumption_Driven_Programming_Jun_2014.png"><img title="Assumption_Driven_Programming_Jun_2014" style="border-top: 0px; border-right: 0px; border-bottom: 0px; border-left: 0px; display: inline" border="0" alt="Assumption_Driven_Programming_Jun_2014" src="/images/files/Assumption_Driven_Programming_Jun_2014_thumb.png" width="350" height="350" /></a> </p>  <p>Obviously, we’re supposed to notice that <a href="https://twitter.com/efleming18" target="_blank">Eric</a> is missing a hand, so he cannot use this newly installed palm scanner. Whoever decided to put in this new interface should have thought of a backup system for Eric or used a different authorization mechanism.</p>  <p>If we step back and think of this in terms of software, we’re talking about making an assumption about our users, data, or how interaction with the system will happen. An example of this would be assuming that your users “all use the start menu”, “all search for programs”, “all use the quick launch bar”, or “all use the desktop”. Each of those is an assumption that Microsoft could make when developing its next version of Windows. Each of those assumptions would be a bad one. Heck, even assuming that I named all of the possibilities already is a really bad assumption. What if someone uses “Run” or PowerShell?</p>  <p>When we’re writing our software, we take a lot of guesses about how the users will use our systems. Don’t! As you’re building, watch them use it. See how they use the system. Ask the user to perform their daily routine in the new software and see what they do. Ask them some questions. And make sure that you check different types of users. Sure, you will not catch every case, but you can avoid a lot of headaches. You might not even have realized that certain users would use the feature you’re building if you don’t ask.</p>  <p>Let’s focus on avoiding this issue for the rest of June.</p>  <p><strong>SPOILER ALERT:</strong> Eric has both a right hand and a left hand… This photo is fake.</p>
