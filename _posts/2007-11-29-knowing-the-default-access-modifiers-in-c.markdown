---
layout: post
title: "Knowing the Default Access Modifiers in C#"
date: 2007-11-29 19:21:00 -0500
comments: true
published: true
categories: ["blog", "Archive"]
tags: ["Blog"]
permalink: "/post/Knowing-the-Default-Access-Modifiers-in-C/"
---
<!-- more -->



<p><a title="512px-Padlock" href="http://www.flickr.com/photos/67369333@N00/2073859235/"><img src="http://static.flickr.com/2261/2073859235_f55f9f639e.jpg" border="0" alt="512px-Padlock" width="240" height="240" align="right" /></a>I have a few friends in college who are learning C# on the side. I've been answering their questions when they ask. One interesting question was regarding access modifiers. I was asked which access modifiers are used by default in certain situations when there is not one specified.</p>
<p>First I'll quickly remind everyone of the access modifiers and what has permission to access them.</p>
<p><strong>private</strong> - Any members of the same class have access.</p>
<p><strong>protected</strong> - Any members of the same class or any derived class have access.</p>
<p><strong>internal</strong> - All code in the same assembly. This means that it doesn't matter where the code is in the assembly. It can be in any class as long as it is inside of the same assembly it has access.</p>
<p><strong>public</strong> - EVERYTHING HAS ACCESS!</p>
<p>When you define a data type of some kind (class, struct, enum, etc.) you need not specify an access modifier, but be aware that the default will be internal. This means that anything else in the assembly has access to it. There is very little sense for it to be private, because that would mean that only it has access to itself which means it would never do <em>anything</em>. Since we like the default permission to be as restrictive as possible it makes sense that the default is internal.</p>
<p><img src="http://static.flickr.com/2135/2074651220_b0da9298bc.jpg" border="0" alt="large_gold_key" width="240" height="243" align="left" />The other code with access modifiers are the members of the types we were just discussing. Since these are within a type private makes sense for them, and since we like keeping this locked down by default they use the private access modifier if no other is specified. This means they are only accessible by other members of the same thing. So a class might have a private member function and that function can only be called by other members of the class; functions, properties, etc.</p>
<p>Protected is probably my favorite access modifier to use, but since it is less restrictive it is not the default. This is because pretty much any time protected can be used so can private so private will be the default. Public is just way to open to be the default and C# doesn't want to encourage programmers to have everything be public. That is just a bad way to write code.</p>
<p>Don't get locked out because you don't know the default access modifier. Make sure you key in to the correct way of writing your code.</p>
<p>Have fun writing code with access modifiers!</p>
