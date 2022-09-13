---
layout: post
title: "Optional and Named Parameters in C#.... Finally"
date: 2008-10-27 22:37:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Orcs Goblins  and .NET"]
permalink: "/post/Optional-and-Named-Parameters-in-C-Finally"
---
<!-- more -->

<p>I've used Python a decent amount in the past. I enjoy the language and I've taught the language to non-computer science students at Kent State University. There are plenty of things that I really love about that language. I could write plenty of blog posts regarding how totally awesome python is. I tend to use it for quick little bits of code. I don't use too much Python for production code, but I do like a lot of the language features.</p>
<p>One of the big pieces of Python I enjoy is the ability to define a default value for a parameter in a method. This allows for optional parameters. Wonderful stuff. I hate having to make extra overloads to handle default parameters which pass in either the right ones or values specifying that the value is missing. Way too much handling just to handle this case.</p>
<p>Named parameters are also a lot of fun since you're able to specify which parameter you're passing. It works pretty well in Python. I don't know how useful it will be in C#, but it is a neat feature which doesn't add much complexity to the language.</p>
<p>In the session I am sitting in at the PDC I am listening to a speaker talking about how this is coming down the pipe for C#. I would guess C# 4.0 will include these features. Now I can finally get rid of all of the extra overloads. I can finally just have my default parameters. No more of the extra overloads or passing in missing values.</p>
<p>For a lot of code we want to allow for customization, but at the same time we want to be able to have default values since the 90% case doesn't require the customization. We need the ability to customize some, so these features in combination could allow a method with say 8 parameters have you specify 2 of them and then name the 3rd one you want to specify. This should help clean up code and allow us to be concerned only with the code which is currently important to us. No need to worry about all the extra parameters in the method that we don't care about.</p>
<p>Finally!!! I've been wanting default and named parameters for a looooong time.</p>
