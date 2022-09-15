---
layout: post
title: "How to Convert from hex to int"
date: 2007-09-12 17:57:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Orcs Goblins  and .NET"]
permalink: "/post/How-to-Convert-from-hex-to-int/"
---
<!-- more -->

<p>I recently needed to convert hexadecimal numbers into integer numbers. So for your benefit, and for mine when I forget how to do this, I will tell you a couple of ways to convert numbers of these types. Both methods are quite simple and easy to use.</p>
<pre class="code"><span>string</span> myHexNumber = <span>"C4FFB716"</span>;
<span>int</span> myIntNumber = <span>Int32</span>.Parse(myHexNumber, System.Globalization.<span>NumberStyles</span>.HexNumber);</pre>
<p>&nbsp;</p>
<p>&nbsp;This will convert a hexadecimal&nbsp;number in string format into an integer number. You could also do the following.</p>
<pre class="code"><span>string</span> myHexNumber = <span>"C4FFB716"</span>;
<span>int</span> myIntNumber = <span>Convert</span>.ToInt32(myHexNumber, 16);</pre>
<p>&nbsp;</p>
<p>In this case you have easily converted from a hexadecimal string into an integer. If you want to convert from a base other than 16 into an integer you can pass either 2 or 8 instead of 16 to this method.</p>
<p>(Yes, I am aware that those are terrible variable names. This is merely an example.)</p>
<p>Enjoy!</p>
