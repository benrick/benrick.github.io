---
layout: post
title: "Commenting Methods Using Liskov Substitution Principle"
date: 2010-08-24 13:00:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Blog", "Blog", "Blog"]
alias: ["/post/Commenting-Methods-Using-Liskov-Substitution-Principle", "/post/commenting-methods-using-liskov-substitution-principle"]
---
<!-- more -->
{% include imported_disclaimer.html %}
<p>After reading the title of this post, some people might be wondering why I am advocating commenting at all, because I&rsquo;ve spoken out <a href="http://brendan.enrick.com/post/When-Should-You-Comment-Your-Code.aspx" target="_blank">against commenting code</a> before. My team and I were recently reading through some code that was littered with comments, and I do mean littered. There were tons, they were mostly useless statements like &ldquo;//run&rdquo;, and I swear there were more of them than actual code. This of course sparked some preaching to our choir about how comments in code are often less-than-useful. We of course settled on the time when they are useful being the XML comments on methods, but those should also only be used when writing public libraries where others will not have access to the source code or unit tests.</p>
<p>Comments on those methods are useful since tons of people will use the method and will not be able to see the guts of the method or examples of how to use it. This makes the comments useful. However, they need to be kept up-to-date (difficult task).</p>
<p>So what does all of this have to do with Listkov Substitution? Well, the principle basically says that all of the classes which implement an interface (or inherit) need to work the same way. There should be no difference between implementations as far as the calling code is concerned. In fact it is really about making sure that we maintain a consistent abstraction. If we say something about the interface it <em>must</em> hold true for the implementation. This means that any comments about the interface must hold true for every implementation.</p>
<p>We were wondering if the comments needed to be on each of the concrete classes or if we could just put it on the interface, and this was confirmed for me by <a href="http://benheimann.com/" target="_blank">Ben Heimann</a> who quickly made an interface and a concrete class. Then he commented just the interface method and not the concrete one. We of course knew we would see the comment when using the interface, but we also saw it when we were dealing with the concrete class. Great work Visual Studio 2010! This means we don&rsquo;t have to duplicate and also signals that we should follow LSP.</p>
<p>The concern is that if you have the comment in both places you would have to update them both. This also means that they could differ, and if they ever needed to intentionally differ then it means that we are violating LSP. Having the comment in the one place should at least point to the fact that we should maintain the same behavior for the calling code in all implementations of our interfaces.</p>
