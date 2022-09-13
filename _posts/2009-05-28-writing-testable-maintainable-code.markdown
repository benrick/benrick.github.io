---
layout: post
title: "Writing Testable, Maintainable Code"
date: 2009-05-28 22:05:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Blog"]
alias: ["/post/Writing-Testable-Maintainable-Code", "/post/writing-testable-maintainable-code"]
---
<!-- more -->

<p>At our company we&rsquo;ve had a few interns start this summer, so we ran a little workshop with the development team to help teach the team a few things about writing tests before writing other code. In our test driven workshop we did some simple problems in teams. We looked at different problems from <a href="http://projecteuler.net/" target="_blank">Project Euler</a>, and solved them in pairs. We all worked out our own tested solutions to the problems and brought them back to discuss. While looking at these we discussed what was good in each one and what could have been done better. We were pairing more experienced testers with the new guys for this exercise.</p>
<p>I think this went very well actually. These might not be production level challenges to work, but the variety of designs gives great insight into what people were thinking and how they were approaching the problem. I was delighted to see that there were small bits of code very similar between designs, but overall none of them really looked similar. Class names here and there might have been the same, but the implementations of classes with the same name could vary wildly.</p>
<p>After we finished with the exercise, we jumped back into teams to continue working. A while later I got into a discussion with one of our full-time developers and an intern where I ended up explaining one of the main reasons we like testing code. There is the obvious security of having the tests, but there is more than just that. One added bonus that not everyone seems to realize is that writing <em>testable</em> code creates some interesting properties in the code.</p>
<p>Why don&rsquo;t we take a look at a few of the properties of <em>testable</em> code. I will certainly not cover all of them, but I will try to get enough to demonstrate my point. (these are in no intentional order)</p>
<h3>A Few Properties of Testable Code</h3>
<ul>
<li>Keeps dependencies to a minimum &ndash; Having fewer dependencies means less mocking, faking, and stubbing. </li>
<li>Follows Single Responsibility &ndash; This keeps things as small pieces which makes for smaller easier to understand and maintain tests. </li>
<li>Programming is done against interfaces &ndash; This allows you to mock and fake these objects, because your code only knows about the interface. </li>
<li>Dependencies are injected into classes &ndash; Without doing this unit testing is impossible and only integration tests could be written. </li>
<li>The code is well documented through the tests &ndash; The tests themselves describe how the code works, and this documentation stays up to date. </li>
</ul>
<p>The neat part about this is the fact that these properties are present in <em>maintainable</em> code as well as <em>testable</em>. I'll sit here a moment while that sinks in..... Yes, you heard right that in order for code to be testable it must also be maintainable. If you ask someone how to write maintainable code, they might be able to spout off some information about theoretically how to do it. What is much harder is actually implementing solutions which are maintainable. This is why testing is important, because if you want to even be <em>able</em> to write the tests, the code first needs to be written in nice decoupled, well-organized ways.</p>
<p>I don't know about you, but I think it is very cool when you see that the properties of testable code seem to coincide with best practices for writing maintainable code.</p>
