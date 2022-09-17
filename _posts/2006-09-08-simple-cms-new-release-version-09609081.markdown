---
layout: post
title: "Simple CMS New Release Version 0.9.60908.1"
date: 2006-09-08 20:47:00 -0400
comments: true
published: true
categories: ["Archive"]
tags: ["Blog"]
permalink: "/post/Simple-CMS-New-Release-Version-09609081/"
---
<!-- more -->



<p>A newer version of <a href="http://aspalliance.com/simplecms">Simple CMS</a> has just been released.&nbsp;The only significant change to Simple CMS is that it now supports sessions. This means that if you have a masterpage you are using with Simple CMS, you may now use the Session object in that masterpage file.</p>
<p><strong>How to enable Session State with HttpHandlers</strong><br />This was an interesting problem,&nbsp;because there isn't a page object in the normal sense of file with aspx as its extension. Normally one can just add enableSessionState = true at the top of the file. In order to achieve this with HttpHandlers you will need to implement System.Web.SessionState.IRequiredSessionState or System.Web.SessionState.IReadOnlySessionState. To do this you simply add one of these as if you are inheriting from a class.</p>
<p>In my case I use an HttpHandlerFactory, so I specified this for the created handler, and not the factory.</p>
