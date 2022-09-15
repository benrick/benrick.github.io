---
layout: post
title: "When Should You Comment Your Code"
date: 2009-10-21 08:44:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Blog"]
permalink: "/post/When-Should-You-Comment-Your-Code/"
---
<!-- more -->

<p>Comment your code when it is hard to understand or determine your intent, because your code is crap. Yep, that is pretty much the best time to comment your code. When I was in college I was told to make sure that I commented my code. I always wondered why. Now I know. Comments really tended to clutter things and make it less clear what I was trying to achieve. I’ve written plenty of comments, but I know that when I use a comment that it means my code sucks.</p>
<p>Comments take time to write, they take up valuable space, they add clutter, and they’re often out of date. So why do we write them? We write them because there is something confusing about some code. Or something that we need to tell future readers about the code.</p>
<p>I very much enjoy being reassured of the way I do things by the books I read. I’ve been reading Code Complete, and it makes me glad they I blatantly disagreed with the people who told me to comment my code. Why? Because the author of the book tells me the exact opposite. I’ve often used the phrase, “code should be self-documenting.” I am not sure from whom or from where I first heard that, but it also affirmed my belief about comments.</p>
<blockquote>
<p>The proper use of comments is to compensate for our failure to express ourself in code. Note that I used the word <em>failure</em>. I meant it. Comments are always failures. We must have them because we cannot always figure out how to express ourselves without them, but their use is not a cause for celebration.</p>
</blockquote>
<p>Aside from the misuse of the English language, that is an excellent paragraph. I’ve never liked writing comments, and I doubt I ever will. It is interesting how some programmers swear by them. I think they are the same programmers who use single-letter variables, magic numbers, and hundred line methods.</p>
<p>I highly recommend reading through the <a href="http://stackoverflow.com/questions/184618/what-is-the-best-comment-in-source-code-you-have-ever-encountered-closed" target="_blank">best comments in source code</a> question on StackOverflow.</p>
<p>Remember kids, anytime you feel the need to write a comment, fix your code instead. You’ll thank yourself down the road. You might be the future developer maintaining the code.</p>
<p>A few steps to follow. (These are the easy ones. Harder ones take more than a bullet point to explain and justify.)</p>
<ul>
<li>Rename variables to more expressive names. </li>
<li>Extract methods so people know what you’re doing. </li>
<li>Extract classes to handle each responsibility. </li>
</ul>
