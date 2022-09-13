---
layout: post
title: "One Reason to Test Before Creating a Method"
date: 2008-12-04 10:18:00 -0500
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Blog"]
alias: ["/post/One-Reason-to-Test-Before-Creating-a-Method", "/post/one-reason-to-test-before-creating-a-method"]
---
<!-- more -->

<p>Most people who know about Test Driven Development have heard the phrase, "Red, Green, Refactor". When it comes to actual implementation of this technique there seems to be a bit of a disagreement. By following the rules of RGR we all agree that we start by writing a failing test (Red), we write the code to make the test pass (Green), and then we make the code better and remove duplication (Refactor). The point of contention I hear about most often is in the Red stage. Some people say to write the failing test before writing <em>any </em>code. Some people say that you can make a skeleton of the code and write the test for that.</p>
<p>In practice I tend to agree with the people that make the skeleton code first. I really just don't like having the compiler error be how my test fails. What I do instead is create the code I am going to test and have it throw a NotImplementedException. This lets me make sure the test is failing so I am sure to flesh out the code.</p>
<p>Now I can certainly see reasons to do both. That is just what I prefer. One interesting problem which can arise from doing my method is the following. Say that I am going to create a new method on a class, so I create the method and write the failing test. Perhaps this is a non-tested project I am working on, so only the new stuff is tested. I write my code and everything passes now. But I've created a new bug. How?</p>
<p>I am kind of cheating here because there is a compiler warning. Since not everyone treats compiler warnings as errors it is certainly possible to have missed this problem. Here is some example code including an extra base class I didn't mention yet.</p>
<div>
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;"><span style="color: #0000ff">class</span> Program
{
    <span style="color: #0000ff">static</span> <span style="color: #0000ff">void</span> Main(<span style="color: #0000ff">string</span>[] args)
    {
        Foo myFoo = <span style="color: #0000ff">new</span> Foo();

        myFoo.Bar();
    }
}

<span style="color: #0000ff">internal</span> <span style="color: #0000ff">class</span> BaseFoo
{
    <span style="color: #0000ff">public</span> <span style="color: #0000ff">void</span> Bar()
    {
        Console.WriteLine(<span style="color: #006080">"Base Bar!!"</span>);
    }
}

<span style="color: #0000ff">internal</span> <span style="color: #0000ff">class</span> Foo : BaseFoo
{
    <span style="color: #0000ff">public</span> <span style="color: #0000ff">void</span> Bar()
    {
        Console.WriteLine(<span style="color: #006080">"Bar!!"</span>);
    }
}</pre>
</div>
<p>So now if I create a method called Bar without realizing there was already one on the parent class I will be hiding the parent one and breaking the existing logic. Since the old code isn't tested I will not know about it. If I had written a test before the code, I would have noticed something odd when the compiler didn't throw an error.</p>
<p>I think it is an interesting debate. Not very important, but interesting. Perhaps people have some more reasons why it should be one way or the other.</p>
