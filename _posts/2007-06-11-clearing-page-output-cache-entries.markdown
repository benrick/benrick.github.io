---
layout: post
title: "Clearing Page Output Cache Entries"
date: 2007-06-11 19:14:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Orcs Goblins  and .NET"]
alias: ["/post/Clearing-Page-Output-Cache-Entries", "/post/clearing-page-output-cache-entries"]
---
<!-- more -->
{% include imported_disclaimer.html %}
<p>Earlier today I had a situation where I needed to clear the output cache entry of a page. After a quick Google search I turned up Steve Smith&rsquo;s Article on <a href="http://aspalliance.com/668_Remove_ASPNET_Page_Output_Cache_Entries">Removing Page Output Cache Entries</a>.</p>
<p>The article is a short, helpful article which quickly and easily explains how to remove the output cache entry of a page.</p>
<p>private void RemoveButton_Click(object sender, System.EventArgs e)<br />{<br />&nbsp;&nbsp;&nbsp; HttpResponse.RemoveOutputCacheItem("/caching/CacheForever.aspx");<br />}</p>
<p>I hope everyone else finds this to be easy to understand and implement. The above should work as long as you have a page named &ldquo;CacheForever.aspx&rdquo; in the folder &ldquo;caching&rdquo; at the root of the site.</p>
<p>Happy Caching!</p>
