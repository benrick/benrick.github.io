---
layout: post
title: "Looking at Testing in Other Fields"
date: 2009-06-12 09:12:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Blog"]
permalink: "/post/Looking-at-Testing-in-Other-Fields/"
---
<!-- more -->

<p>Software development is not alone in the world. Surprised aren't you? There are other fields which exist. Most of these fields have been around much longer than we have, and sadly they tend to do things better than we do in a lot of ways. Heck they're much more mature than we are. I am not saying there is anything wrong with how we are doing things, but I do believe that our field can grow and develop a great deal still. We need to be looking at these other fields though and see how they do things. We need to take what they do and apply what we do well in order to become truly great.</p>
<p>A lot of people have read about "The Toyota Way". In fact it is on my reading list, and I plan on getting to it sometime soon. There is a lot than can be learned from other industries I believe. Lean thinking works no matter what field you're in. From the Wikipedia entry on this topic we can find this as "Principle 8".</p>
<blockquote>
<p>Use only reliable, thoroughly tested technology that serves your people and processes.</p>
</blockquote>
<p>Now can someone tell me what the 5th word is in this quote? Yes, that is correct. The word is "tested". Think about how cars are made here for a minute. Why don't we start at the high level and work our way down. We will start with our full system integration tests.</p>
<p><strong>The car crash test:</strong> When test crashing a car there is no one behind the wheel. Why? I know of at least two reasons; it is dangerous and more importantly it needs to be identical every time. So what do they do?<em> They have a test harness in place that allows them to automate the test yielding an identical test every time.</em> They could have remote controlled the cars or something, but that would allow for too much human error.</p>
<p><strong>Testing individual pieces:</strong> The different components of cars are tested for defects. Usually there is some machine that comes along and does something like applying pressures in a stress test. They could have a person go out and apply the same tests, but they don't. Why? <em>If you're trying to have a consistent test it must be automated. </em>Is that the only reason? Of course it is not. <em>Automated tasks are also much, much faster. Machines are much faster than humans.</em></p>
<p>So aren't all of these machines expensive? Yes, of course they are. Don't you think it is expensive to build a machine that crashes cars? It is also expensive to have to crash perfectly good cars just to see how they respond in an accident.</p>
<p><strong><em>Software test harnesses are not expensive. They are code. What happens if you try to make your code throw an exception while in a test harness? NOTHING. You run the code again.</em></strong></p>
<p>Testing software is cheap. Other industries test there stuff as well. They aren't testing in the same way we do. Why? Because we have this huge advantage they don't. Our test harnesses are just software. Our stuff is cheap and reusable. We can run our tests all the time and the only resource we use is electricity. Much cheaper than the rubber and steel the car industry needs.</p>
