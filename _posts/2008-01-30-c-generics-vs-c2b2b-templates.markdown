---
layout: post
title: "C# Generics vs C++ Templates"
date: 2008-01-30 14:44:00 -0500
comments: true
published: true
categories: ["blog", "Archive"]
tags: ["Blog"]
permalink: "/post/C-Generics-vs-C2b2b-Templates/"
---
<!-- more -->



<p>I regularly meet with a group of my college friends with whom I studied Computer Science. While at a great local <a href="http://www.raysplacekent.com/" target="_blank">bar</a> we have plenty of interesting computer-related conversations. A lot of .NET developers probably spend most of their time discussing technical topics with other .NET developers. Our conversations are much more interesting because everyone there works with different languages and different types of technology. It really adds a lot to our discussions. So as has happened a few times, I mentioned C# Generics. As usual it sparked a conversation about how C# Generics are not as good as C++ Templates. As usual I agree with them. (Yes, I really do like C++ templates better than I like Generics in C#)</p>
<p>So I searched on MSDN, because I wanted to see what Microsoft cites as the key differences between C++ templates and C# Generics. I found this article explaining <a href="http://msdn2.microsoft.com/en-us/library/c6cyy67b.aspx" target="_blank">the differences between C++ templates and C# Generics</a>. OK, I agree these are some important differences. It says on there specifically that they were not even trying to have as much functionality as templates. It is good that they said that, because the list of "differences" could be renamed "reasons why templates are better".</p>
<p>The list of reasons cites a bunch of differences in how they are able to be <em>used. </em>I still want to know the differences in the implementation of them. For that big important difference they have it separated from the nice list. Its in the paragraph of description. They mention one HUGE difference. As they say, "C# generic type substitutions are performed at runtime and generic type information is thereby preserved for instantiated objects." So what is the big deal you might say. There are good things and bad things here for generics.</p>
<p>Since templates are compiled at runtime, the compiler will figure out every version of the template it needs and will create the code for them. This is great because it gives optimal performance. Sure there is a bit more code, but it is nice to not have to create these methods at runtime. With C# Generics, the required code is created at runtime. Ok so that sounds pretty bad. It isn't really as bad as it sounds. Generics are implemented smartly, and because of this it isn't much of a performance issue. So at runtime our code will be created to handle the different types our generic can handle. What if we're going to have a bunch of types? If they're all value types then you could have a problem. It will actually create a completely new implementation of your code for every value type you use for the generic. If you're using a reference type it uses some cool tricks to point to the correct type, so it only has to have one reference type implementation. This means you'll have the performance hit once when you first need the generic on a reference type. Then it is a minimal hit each other time you need it.</p>
<p>Yes, I was a C++ programmer before I learned C#. I hope you enjoyed this post. I appreciate comments. I really like the ones which add something to the post, so if you've got extra information to add I encourage you do so. If I've made any mistakes in this, please let me know.</p>
