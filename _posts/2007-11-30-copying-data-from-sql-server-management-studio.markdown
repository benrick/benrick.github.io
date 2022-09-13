---
layout: post
title: "Copying Data From SQL Server Management Studio"
date: 2007-11-30 18:16:00 -0500
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Orcs Goblins  and .NET"]
alias: ["/post/Copying-Data-From-SQL-Server-Management-Studio", "/post/copying-data-from-sql-server-management-studio"]
---
<!-- more -->

<p>I often write queries in SQL Server Management Studio to find different bits of information about which I am curious. This is quite easy and I discover a lot of useful and interesting things this way. You might ask why I am writing this blog post. I'll first say that I try to share these little tidbits with others. Sure I could bring people over to my computer and show them these nifty collections of data with certain meanings, but that would just be silly. I need to store it elsewhere and email it.</p>
<p>Maybe I'm just going about things the wrong way, but I've tried to copy and paste from SSMS into Outlook and that doesn't usually work well. Outlook doesn't seem to figure out that I would like my data pasted as a table, so I usually throw it into Excel first. Doing this will get my data into a nice tabular format.</p>
<p>Now that I've finally gotten my tabular data into a table everything is great. Right? No. I lose once again. I don't have the column names with my data so I end up with something like this and without column names people will not know what I am trying to tell them.</p>
<table border="0" cellspacing="0" cellpadding="2">
<tbody>
<tr>
<td>Brendan</td>
<td>McAwesome</td>
<td>Enrick</td>
<td>5555555555</td>
<td>12345</td>
<td>9876543</td>
</tr>
<tr>
<td>John</td>
<td>Michael</td>
<td>Smith</td>
<td>1234678910</td>
<td>1337</td>
<td>31337</td>
</tr>
</tbody>
</table>
<p>So then I have to go and type out column names so that the people I send this to know what it is. Now for this example it wouldn't be too bad, but sometimes I'll be sending 10 columns worth of data and that is just annoying. I wish I could just copy out of SQL Server and have it pull column names at least then my Excel trick would at least work. If anyone knows a nice easy way to just copy out of SSMS please let me know it would make things so much easier.</p>
<p>Perhaps you can find some elusive option names similarly to <em>Copy All Data With Column Names</em>, because I sure as hell haven't found it.</p>
<p>In case you are wondering those column names are; <em>FirstName</em>, <em>MiddleName</em>, <em>LastName</em>, <em>Phone</em>, <em>SomeValue</em>, <em>SomeOtherValue</em>.</p>
