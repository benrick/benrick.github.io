---
layout: post
title: "Separation of Code Responsibilities"
date: 2008-09-16 20:18:00 -0400
comments: true
published: true
categories: ["blog", "Archive"]
tags: ["Blog"]
permalink: "/post/Separation-of-Code-Responsibilities/"
---
<!-- more -->



<p><img src="http://images.amazon.com/images/P/0131177052.01.MZZZZZZZ.jpg" alt="" align="right" /></p>
<p>One book I would highly recommend reading is <a href="http://www.amazon.com/Working-Effectively-Legacy-Robert-Martin/dp/0131177052" target="_blank">Working Effectively with Legacy Code</a>.&nbsp; I should write a review of this book at some point, but for now I just want to mention one great thing about it. Reading the book is very valuable, but it is an excellent reference book. Many of the chapters of the book are devoted to certain scenarios which might arise when dealing with legacy code. It then goes on to explain how to handle these situations.</p>
<p>At the moment I am attempting to change some code which needs to make a bunch of API calls. Right now the code is not neatly written and methods are directly interacting with the API, performing in-memory work, and calling methods to save data. Since I am relatively new to this stuff, I figured I'd read the chapter titled, "My Application Is All API Calls".</p>
<p>In the chapter, the author uses a simple example about a mailing list server. The application is a big jumbled up mess. As the text preempting the code states, "We're not even sure it works". This type of situation is exactly what I am trying to avoid, and a great way to <em>know something works</em> is to have tests written for it which demonstrate the code's ability to function correctly. The tests are also a great way to show what a piece of code <em>does</em>.</p>
<p>When the author is discussing how to design the application in a better way, he mentions his desire to separate the code's responsibilities. Now I know that separating code responsibilities is important, but his example really shows it well I think.</p>
<blockquote>
<p>1. We need something that can receive each incoming message and feed it into our system.</p>
<p>2. We need something that can just send out a mail message.</p>
<p>3. We need something that can make new messages for each incoming message, based on our roster of list recipients.</p>
<p>4. We need something that sleeps most of the time but wakes up periodically to see if there is more mail.</p>
</blockquote>
<p>The nice thing is it then becomes so much easier to work with the API calls because they've so nicely been separated. One mistake I've made in the past is not separating out the code which needs to periodically perform some other action. I have attempted in the past to link that together with the code performing the local work. BIG MISTAKE!</p>
<p>Right now what I am planning on writing is going to have these separate responsibilities:</p>
<ol>
<li>Something to fetch data from an external source.</li>
<li>Something to manipulate the retrieved data into its desired format.</li>
<li>Something to store the data internally.</li>
<li>Something to periodically check for new data.</li>
</ol>
<p>Notice the incredible similarity there. It is very nice for my application, because only one piece needs to know about the API, and only one piece needs to know how the data is stored. Instead of before where some of that was a bit muddled together. This separation keeps the code cleaner and much easier to code. Testing will also be a lot easier because of this separation.</p>
<p>One of the most difficult parts about testing code well, is that lots of code is not separated well enough to be tested. Being too tightly connected to an API makes code nearly impossible to test, so it is hard to tell if a piece of code is working or what it does.</p>
