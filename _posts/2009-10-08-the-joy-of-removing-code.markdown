---
layout: post
title: "The Joy of Removing Code"
date: 2009-10-08 16:25:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Blog"]
permalink: "/post/The-Joy-of-Removing-Code/"
---
<!-- more -->

<p>Removing code is one of my favorite activities. Isn&rsquo;t it one of yours? As a software developer I strive to write less code. Sounds kind of funny, but what I mean is that I want the code that I write to be reused as effectively as possible. Having less code means that maintenance is easier. I can fix things faster, change things faster, find things faster, and figure things out faster.</p>
<p>This is a very good case of &ldquo;less is more&rdquo;, which is one reason why I love removing code. I really enjoy getting more or even equivalent work done with less code.</p>
<p>I just finished eliminating a constructor. Why? Well, it really was not needed. As it turns out there was a more appropriate constructor to use for the class. Not sure when or why the constructor was created, but it doesn&rsquo;t really matter. I am fairly certain that nothing is using it after my removing it. Code still compiles. Tests still pass.</p>
<p>This does a lot of good things. It makes the class less intimidating by dropping the line count. It makes clearer which constructor to use when there are fewer of them. If I need to make a change to the constructor by either adding or removing a parameter for example there is only one place to do this now. Before there were two places.</p>
<p>I love writing code, but I also enjoy removing excess code. It just makes things simpler, which is exactly how I like things. I want my code to be just complex enough to work. When I am refactoring old code this is one of the best things to do. Chopping off all the bits and pieces of unneeded legacy code is progress.</p>
<p>Has anyone else removed any code recently they were glad to be rid of? Anyone eliminate any entire class libraries or anything cool like that?</p>
<p>&ldquo;Do you want complexity with that?&rdquo;</p>
<p>&ldquo;No, thank you.&rdquo;</p>
