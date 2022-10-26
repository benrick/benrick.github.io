---
layout: post
title: "Dangers of Using Floating Point Numbers"
date: 2007-09-25 15:55:00 -0400
comments: true
published: true
categories: ["Archive"]
tags: ["Blog"]
permalink: "/post/Dangers-of-Using-Floating-Point-Numbers/"
---
<!-- more -->



<p>An interesting question came up from a few of my students while teaching <a href="/post/Teaching-Introduction-to-Computer-Programming/">my class</a>. Some of them discovered a bug in their programs which they did not understand. They were writing a program which was doing some calculations on currency.</p>
<p>Computer Programmers commonly use floating point numbers, but I am sure that not all of them really understand what is going on underneath the hood. As I am sure everyone reading this knows, all data is stored in binary format on computers. In base 10 as with all numbering systems with a base, each digit is a round number in the base. The fractional amounts are what is interesting and specific to floating point numbers and not to integers.</p>
<p>When using floating point numbers they aren't stored in a way which is intuitive to base 10 users. As an example I will use the fractional amount 1/4. To make seeing the conversion easier I'll say that it is also 25/100 or really 2/10 + 5/100.</p>
<p>In a base 10 floating point number we may represent this number as the following.</p>
<p>0.25</p>
<p>If we were to write that same number in binary format we should note that it is 1/4 or really 0/2 + 1/4.</p>
<p>0.01</p>
<p>You'll want to notice here that those two numbers are not similar, and as you can probably guess, some examples would not come out quite so cleanly.</p>
<p>The problem which the students came across stemmed from subtracting&nbsp;10 cents&nbsp;from some amount of money. I'll use $100.00 as my example. When the students did the calculation it worked in the following way:</p>
<p>100.00 - 0.1 = 99.900000000000006</p>
<p><img src="http://static.flickr.com/1088/1452877225_08cf99c95b.jpg" border="0" alt="FloatingPointError" /></p>
<p>That seems to not make sense, but it does make some sense. There are numbers which in base 10 will have decimal places which will extend on, and we have to round them at some point. A good example of this is 1/3 which can be written roughly as any of the following</p>
<p>0.3</p>
<p>0.33</p>
<p>0.33333333333</p>
<p>All of those are approximations of that fractional amount. In binary we have the same type of problem, because 0.1 cannot be represented correctly in binary.&nbsp;This causes a problem; it will round at a certain point, and because the number isn't represented correctly, the calculation is done incorrectly. In many other languages it hides away that inaccuracy, but Python allows you to see it.</p>
<p>It is important to know how your floating point numbers are working underneath. Be careful. The computer doesn't speak our language.</p>
