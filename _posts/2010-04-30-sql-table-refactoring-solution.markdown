---
layout: post
title: "Sql Table Refactoring Solution"
date: 2010-04-30 16:02:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Blog"]
permalink: "/post/Sql-Table-Refactoring-Solution/"
---
<!-- more -->

<p>Steve Smith posted an interesting <a href="http://stevesmithblog.com/blog/sql-table-refactoring-challenge/" target="_blank">SQL Table Refactoring Challenge</a> on his blog. I am prepared to go out on a limb and share my solution for how to make a table more efficient.</p>
<p>The first step I would take is to change the columns of the table a little bit.</p>
<ul>
<li>Change CountryCode to a char(2) since they are all 2-character ISO standards. The varchar does limit itself based on the size of the data, but has an overhead of 2 bytes. This will also prevent anything longer from being entered into the table.</li>
<li>If you&rsquo;re feeling very ambitious you can make a CountryId column that is of type smallint and uses the id of the country instead of the 2-characters. <em>This will require an update to all of the existing data so I would say this isn&rsquo;t worth the effort.</em></li>
<li>AboveFold can be changed to a tinyint. <strong>Note: these values are 0 to 255 so we will need to remap the values in the database.</strong></li>
<li>A smallint can be used for the Clicks column, since it doesn&rsquo;t need to get very large.</li>
<li>Period can change to a date. This will take up 3 bytes which is much smaller than the 8 for the datetime.</li>
</ul>
<p>As an extra note I believe that int is required to get up to 50,000 for the tables which require it. If we could drop the limit to around 30000 we could use a smallint for those.</p>
<p>Once I have that table created I create 2 duplicate tables (duplicated schema not all of the data). [lq_ActivityLogLoad] and [lq_ActivityLogLoadNext] At any given time we will write to one of these two tables and not the huge table.</p>
<p>Then I create a job which will switch to which of these two tables we are writing. After switching the job will load all of this data directly into the large table using an Upsert (Update or Insert). After loading the data from the table it can empty out that load table and wait a minute and perform this action over again. Doing this loading pattern will make it so the writes will be on these small tables which aren&rsquo;t being read from.</p>
<p>I would change the primary key to be based on the ID and put a unique non-clustered index on the columns currently used for the primary key preserving the safety from the unique constraint.</p>
<p>Here is the table I created for this.</p>
<div>
<pre id="codeSnippet" style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff">CREATE</span> <span style="color: #0000ff">TABLE</span> [dbo].[lq_ActivityLog](<br />    [ID] [bigint] <span style="color: #0000ff">IDENTITY</span>(1,1) <span style="color: #0000ff">NOT</span> <span style="color: #0000ff">NULL</span>,<br />    [PlacementID] [<span style="color: #0000ff">int</span>] <span style="color: #0000ff">NOT</span> <span style="color: #0000ff">NULL</span>,<br />    [CreativeID] [<span style="color: #0000ff">int</span>] <span style="color: #0000ff">NOT</span> <span style="color: #0000ff">NULL</span>,<br />    [PublisherID] [<span style="color: #0000ff">int</span>] <span style="color: #0000ff">NOT</span> <span style="color: #0000ff">NULL</span>,<br />    [CountryCode] [<span style="color: #0000ff">char</span>](2) <span style="color: #0000ff">NOT</span> <span style="color: #0000ff">NULL</span>,<br />    [RequestedZoneID] [<span style="color: #0000ff">int</span>] <span style="color: #0000ff">NOT</span> <span style="color: #0000ff">NULL</span>,<br />    [AboveFold] [tinyint] <span style="color: #0000ff">NOT</span> <span style="color: #0000ff">NULL</span>,<br />    [Period] [<span style="color: #0000ff">date</span>] <span style="color: #0000ff">NOT</span> <span style="color: #0000ff">NULL</span>,<br />    [Clicks] [<span style="color: #0000ff">smallint</span>] <span style="color: #0000ff">NOT</span> <span style="color: #0000ff">NULL</span>,<br />    [Impressions] [<span style="color: #0000ff">int</span>] <span style="color: #0000ff">NOT</span> <span style="color: #0000ff">NULL</span>,<br /><span style="color: #0000ff">CONSTRAINT</span> [PK_lq_ActivityLog] <span style="color: #0000ff">PRIMARY</span> <span style="color: #0000ff">KEY</span> <span style="color: #0000ff">CLUSTERED</span> <br />(<br />    [ID] <span style="color: #0000ff">ASC</span><br />)</pre>
</div>
<div>&nbsp;</div>
<div><br /></div>
