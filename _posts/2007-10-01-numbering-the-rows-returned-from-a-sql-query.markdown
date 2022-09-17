---
layout: post
title: "Numbering the Rows Returned from a SQL Query"
date: 2007-10-01 22:06:00 -0400
comments: true
published: true
categories: ["Archive"]
tags: ["Blog"]
permalink: "/post/Numbering-the-Rows-Returned-from-a-SQL-Query/"
---
<!-- more -->



<p>Outside of SQL it would be quite easy to number the rows returned from query, but to do so inside of the SQL is a bit more difficult. I recently wanted to be able to number the rows returned from a query in a stored procedure. I am using SQL Server 2000, so I cannot use row_number().</p>
<p>I was going to ask my go to SQL guy, <a href="http://sqladvice.com/blogs/gstark/default.aspx">Gregg Stark</a>, how to do this, but while in the process of asking him for a good method of doing this, I came up with the solution. My cool trick for numbering the rows returned from a query is useful because I don't actually want to return these rows to other code. I want to store them back into my database ordered differently than the numbering, and using a table variable will allow me to do exactly what I am trying to do.</p>
<p>First we need to create a table variable. We will define that table as having an identity column plus any other columns we happen to need. We then insert into that table all of the values returned from our query.</p>
<div style="font-size: 8pt; margin: 20px 0px 10px; overflow: auto; width: 97.5%; cursor: text; max-height: 200px; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border: gray 1px solid; padding: 4px;">
<div style="font-size: 8pt; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;">
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: white; border-style: none; padding: 0px;"><span style="color:#0000ff;">declare</span> @t <span style="color:#0000ff;">table</span> (Rank <span style="color:#0000ff;">int</span> <span style="color:#0000ff;">identity</span>(1,1), UserName nvarchar(256), Points <span style="color:#0000ff;">int</span>)</pre>
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;">insert <span style="color:#0000ff;">into</span> @t</pre>
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: white; border-style: none; padding: 0px;"><span style="color:#0000ff;">select</span> UserName, <span style="color:#0000ff;">sum</span>(PointsEarned) <span style="color:#0000ff;">as</span> Points</pre>
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;"><span style="color:#0000ff;">from</span> UserRecognition</pre>
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: white; border-style: none; padding: 0px;"><span style="color:#0000ff;">group</span> <span style="color:#0000ff;">by</span> UserName</pre>
</div>
</div>
<p>After running this part we have created a table variable which contains the information we want. We can then select data out of this as if it were a normal table. In this example I am able to obtain a ranking for my users based on their earned points. This lets me store that ranking without having them stored in ranking order.</p>
<p>It is obviously much easier to do this in SQL 2005, but this is a very cool trick for those of us using SQL Server 2000. Let me know what you think, and if you have any cool improvements.</p>
