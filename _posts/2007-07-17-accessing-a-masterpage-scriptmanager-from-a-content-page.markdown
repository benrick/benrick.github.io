---
layout: post
title: "Accessing a MasterPage ScriptManager from a Content Page"
date: 2007-07-17 16:58:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Orcs Goblins  and .NET"]
alias: ["/post/Accessing-a-MasterPage-ScriptManager-from-a-Content-Page", "/post/accessing-a-masterpage-scriptmanager-from-a-content-page"]
---
<!-- more -->

<p>Recently I had forgotten how to access the ScriptManager in my MasterPage from one of the Content Pages. There is a static method on the ScriptManager class called GetCurrent() which will allow access to the current instance of a ScriptManager. This is useful because the ScriptManagerProxy is really just designed to do the declarative work normally performed on the ASP.NET page, but some work needs to be done through code. An example would be to check the ScriptManager instances IsInAsyncPostback property.</p>
<p>if (ScriptManager.GetCurrent().IsInAsyncPostback)</p>
<p>{</p>
<p>&nbsp;&nbsp;&nbsp; // Perform only in asynchronous postback logic here.</p>
<p>}&nbsp;</p>
<p>This is very useful and easy, but I seem to always forget it is here. Perhaps now that I have blogged about it I will remember, and if not I can at least come back here to find it. Yes, when I forget I go through the trouble of casting Master as my MasterPage's class and then I access it that way (what a pain).</p>
