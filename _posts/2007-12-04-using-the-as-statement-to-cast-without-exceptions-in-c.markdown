---
layout: post
title: "Using the as Statement to Cast Without Exceptions in C#"
date: 2007-12-04 02:58:00 -0500
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Orcs Goblins  and .NET"]
permalink: "/post/Using-the-as-Statement-to-Cast-Without-Exceptions-in-C"
---
<!-- more -->

<p>It is common to obtain variables with a type which is not the desired one. Considering that plenty of times there will be variables passed using the <em>object</em> data type, it is important to be able to cast your variables into more usable types. Say for example you're passed a variable as an <em>object</em>. You probably want to be able to access properties or methods of this <em>object</em>, so you will need to cast it into another class. The simple way of doing this is to use code similar to this.</p>
<pre class="code"><span>DataTable</span> myData = (<span>DataTable</span>)dataSource;</pre>
<p><a href="http://11011.net/software/vspaste"></a>This works well, but is slightly more dangerous than it needs to be. The problem I have with casting it in this way is that the variable <em>dataSource</em> might not be a <em>DataTable</em>, and if this is the case we will throw an exception. Yes, we could wrap a <em>try-catch</em> block around this code, but I prefer to avoid exceptions when possible instead of catching them.</p>
<p>If we use the <em>as</em> statement we will be able to achieve the same result and just need a little bit of checking for an error. This way if our code is in an exceptional case we can handle it ourselves instead of having the overhead of a <em>try-catch </em>block. If the <em>as</em> statement receives an invalid cast it does not throw an exception. Instead of throwing the exception it merely places the null value instead. Since we receive the null value if the cast fails, we are now able to simply check for the null value.</p>
<pre class="code"><span>DataTable</span> myData = dataSource <span>as</span> <span>DataTable</span>;
<span>if</span> (myData != <span>null</span>)
{
    <span>// Perform work here
</span>}
<span>else
</span>{
    <span>// Error handling code goes here. Perhaps a message of some kind.
</span>}</pre>
<p>As you can see we're able to avoid our exception and handle it without using a <em>try-catch</em> block. I am not advocating programs without these <em>try-catch </em>blocks. I am merely saying that I find it better to avoid catching exceptions that could have been avoided in the first place. I think some people become excessive with <em>try-catch </em>blocks. I've seen plenty of people write code which doesn't check strings for validity they instead just try working with them and if an exception occurs they catch it and respond. I think it is simply crazy.</p>
<p>Have a great day! Happy casting!</p>
