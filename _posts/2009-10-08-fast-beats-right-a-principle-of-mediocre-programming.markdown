---
layout: post
title: "Fast Beats Right, a Principle of Mediocre Programming"
date: 2009-10-08 15:19:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Blog"]
permalink: "/post/Fast-Beats-Right-a-Principle-of-Mediocre-Programming"
---
<!-- more -->

<p>Steve Smith just posted an interesting set of anti-principles, anti-patterns, and anti-practices that make up <em><a href="http://stevesmithblog.com/blog/principles-patterns-and-practices-of-mediocre-programming/" target="_blank">mediocre programming</a></em>. In the post one of the principles of mediocre programming that Steve mentions is,</p>
<blockquote>
<p><strong>Fast Beats Right (FBR)</strong> &ndash; It&rsquo;s more important to get something done that probably works, or that works right now even if it will be hard to change later, than to spend time ensuring that it is correct or is well designed.</p>
</blockquote>
<p>I think we&rsquo;ve all seen people who code this way before. They&rsquo;ll get the really quick, dirty solution in place. Steve also makes note of what he has experienced as management&rsquo;s opinion of this behavior.</p>
<blockquote>
<p>sometimes management may be OK with dictating that for a given feature or prototype, speed is more important than anything else</p>
</blockquote>
<p>The really scary part here is that there are managers who think that <strong><em>faster == better</em></strong>. Some teams have programmers following this principle and the managers think those are the best programmers. Why? Well, that guy gets lots of new stuff done. These other guys don&rsquo;t (because they have to clean up the crap the fast guy writes.) Sure, for any task that is small enough I can do the work really quickly without testing or structuring things correctly. However, it might not work for all cases. The code could be fragile. It is very hard to determine how well it will stand up. Down the road I might need to add on to that code, and it could be so bad that it needs to be completely rewritten.</p>
<p>I really hope that no one is stuck at an office where management believes that an FBR programmer is a good programmer.</p>
<p>Have you every worked with a coder like this? What was the opinion of developer from the management point of view?</p>
