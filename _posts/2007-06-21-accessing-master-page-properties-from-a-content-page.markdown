---
layout: post
title: "Accessing Master Page Properties from a content page"
date: 2007-06-21 18:05:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Orcs Goblins  and .NET"]
permalink: "/post/Accessing-Master-Page-Properties-from-a-content-page/"
---
<!-- more -->

<p>As I mentioned in my previous blog post about <a href="http://brendan.enrick.com/post/Accessing-Properties-of-a-Base-Page-from-a-User-Control.aspx" target="_blank">Accessing a property of a base page from a user control</a>, I am going to explain how to access a property on a MasterPage from the content page. One merely has to check the namespace and the class name of the masterpage, which can be found in the code behind file. Just cast the Content Page&rsquo;s Master as the class of the masterpage file which it uses, and then just access the value. It is really quite simple.</p>
<blockquote style="margin-right:0px;" dir="ltr"><span style="color: #0000ff; font-size: x-small;"> </span>
<p><span style="color: #0000ff; font-size: x-small;">int</span><span style="font-size: x-small;"> neededValue = ((MyNameSpace.MyMasterPageClassName)Master).MyProperty;</span></p>
</blockquote>
<p dir="ltr"><span style="font-size: x-small;">Using that method you are able to easily access a property of a masterpage file when needed.</span></p>
