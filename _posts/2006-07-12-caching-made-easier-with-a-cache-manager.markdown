---
layout: post
title: "Caching made easier with a cache manager"
date: 2006-07-12 15:02:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Orcs Goblins  and .NET"]
alias: ["/post/Caching-made-easier-with-a-cache-manager", "/post/caching-made-easier-with-a-cache-manager"]
---
<!-- more -->

<p>&nbsp;&nbsp;&nbsp;I recently added caching to my Content Management System. Since I am no caching expert I wanted to make sure I had created the functionality that I wanted to make. I wanted to ensure durations were as I expected, and wanted to make sure that items were cached when they should be and removed when they shouldn&rsquo;t be cached anymore. I could have changed the program to debugging mode and debugged the code. I could also have added code to check and see the values of the cache object at certain times, but I found a much easier solution.</p>
<p>&nbsp;&nbsp;&nbsp;I found that by adding this <a href="http://aspalliance.com/cachemanager/" target="_blank">Cache Manager</a>&nbsp;plug-in to my site I was able to quickly and easily check at any moment what was in the cache. All it took to add this to my site was copying this file into my bin folder, and copying a line of code into my web.config file. Since I was just using this while debugging the application there was no need to worry about the optional security on the cache manager. When I was done setting up the caching, I simply removed the dll file and the line of code from my web.config file.</p>
<p>&nbsp;&nbsp;&nbsp;I recommend checking out that cool little plug-in if you are doing any work with caching. I plan to use that tool any time I am working with caching on any ASP.NET web site. I like things that make my job easier.</p>
