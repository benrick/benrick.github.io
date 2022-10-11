---
layout: post
title: "Time-Tested Testing Tips – Part 6"
date: 2009-08-19 08:42:00 -0400
comments: true
published: true
categories: ["Archive"]
tags: ["Unit Testing"]
permalink: "/post/Time-Tested-Testing-Tips-e28093-Part-6/"
---

<p>If you haven&rsquo;t seen my earlier posts on this topic. I&rsquo;ve mentioned a bunch of tips which should make your testing easier and more effective. If you&rsquo;re looking for more tips check out these previous posts.</p>
<p><a href="/post/2009/05/19/Time-Tested-Testing-Tips-Part-1.aspx" target="_blank">Time-Tested Testing Tips - Part 1</a></p>
<p><a href="/post/2009/05/19/Time-Tested-Testing-Tips-Part-2.aspx" target="_blank">Time-Tested Testing Tips - Part 2</a></p>
<p><a href="/post/2009/05/20/Time-Tested-Testing-Tips-Part-3.aspx" target="_blank">Time-Tested Testing Tips - Part 3</a></p>
<p><a href="/post/2009/05/21/Time-Tested-Testing-Tips-Part-4.aspx" target="_blank">Time-Tested Testing Tips - Part 4</a></p>
<p><a href="/post/2009/06/08/Time-Tested-Testing-Tips-Part-5.aspx" target="_blank">Time-Tested Testing Tips - Part 5</a></p>
<h3>Don&rsquo;t Repeat Yourself</h3>
<p>I am sure a lot of you have heard this before and know that Don&rsquo;t Repeat Yourself (DRY) means that you should reuse code so that you&rsquo;re not repeating the same code all of the time. This also applies to testing. Sure we know to extract the logic in our tests, because we know that <a href="/post/treat-your-tests-well/" target="_blank">test code should be treated very well</a>.</p>
<p>I am not talking about the logic in your tests not being repeated. I am saying that you should not test the same thing twice. Try to only test each thing once. This makes identifying the issue a lot easier. This is extremely important for edge cases. Make sure you&rsquo;re only testing your edge cases in your edge case test.</p>
<p>You should have a test for each edge case and preferably it is the only test using parameters for the edge case. If something else is using it you&rsquo;re creating difficulties in maintenance as well as tracking down bugs.</p>
<p>If you break a piece of code dealing with an edge case it will be harder to track down since two tests will be failing as a result. If there were only one it would be easier to find and fix the issue. Also there is the simple fact that <em>things change</em>. What happens if later on the desired logic of the program changes and the handling of the edge case changes. Well now you have to change the code in two places instead of just the one. This makes it more difficult to change the logic of your program. repetition == bad</p>
<h3>Start Writing Tests For Everything</h3>
<p>When you&rsquo;re going to try some new piece of code how do you go about it? I am sure a lot of people will create a small sample Console Application and try something and have it print out results to the Console. This works very well, but if you&rsquo;re really trying to pick up testing you should try writing a test instead. If you want to see how some new functionality works give it a shot in a test. Write a test to see what happens. Assert on the results and try to predict the output. This is a fun little way to work with things and you&rsquo;ll get more experience using your testing framework.</p>
<p>It is important when learning to write tests that you do it as often as possible. Get used to writing them whenever you write code, so when you&rsquo;re looking at something new you might as well look at it with a test. What better way to &ldquo;test it out&rdquo; than using your unit tests to do it.</p>
<p>Have a great day! Keep testing!</p>
