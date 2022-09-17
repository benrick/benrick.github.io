---
layout: post
title: "Change SQL Server Instance for Visual Studio Database Project"
date: 2008-04-02 21:39:00 -0400
comments: true
published: true
categories: ["Archive"]
tags: ["Blog"]
permalink: "/post/Change-SQL-Server-Instance-for-Visual-Studio-Database-Project/"
---
<!-- more -->



<p>While installing SQL Server 2005 recently I ran into some <a href="/post/SQL-Server-Client-Tools-Installation.aspx" target="_blank">difficulty</a>. I use database projects from Visual Studio 2005 Team Edition for Database Professionals. I use Visual Studio 2008 with them now, and I recently made a mistake while using one of these projects. When I ran this project my default instance of SQL Server was not listed, so I figured I would connect it to the SQL Express. <strong>BIG MISTAKE</strong>. After installing SQL Server and getting it working correctly I removed SQL Server Express, and now the real fun begins. The database project no longer loads.</p>
<p>So I try removing and adding the project in my solution figuring it might prompt me for the database instance again. No luck. So I decide to ask around a bit. One <a href="http://forums.microsoft.com/MSDN/ShowPost.aspx?PostID=3105971&amp;SiteID=1" target="_blank">forum</a> got me a nice response. It explained how to make the change as well as linking to this MSDN article.</p>
<p><a title="http://msdn2.microsoft.com/en-us/library/aa833159(VS.80).aspx" href="http://msdn2.microsoft.com/en-us/library/aa833159(VS.80).aspx">http://msdn2.microsoft.com/en-us/library/aa833159(VS.80).aspx</a></p>
<p>To make this change you just have to alter some settings in Visual Studio. Start by navigating to the Tools menu and choose Options.</p>
<p><img src="http://static.flickr.com/3090/2383732380_f7c679b561.jpg" border="0" alt="SetValidationDatabase-Step1" /></p>
<p>Once you've opened the Options menu, navigate to the Database Tools section and pick Design-time Validation Database. This is the information for the database used by Visual Studio for database projects. Change the SQL Server Instance Name to whatever the name of the local database is.</p>
<p><img src="http://static.flickr.com/2328/2382903109_87a9b1ef00.jpg" border="0" alt="SetValidationDatabase-Step2" /></p>
<p>I made the bad assumption of assuming that the <em>project</em> is what connects to the server instead of Visual Studio. I checked everywhere in settings for the project, but it slipped my mind that Visual Studio would be what would contain that setting.</p>
<p>As one final note I will say Googling sucks when you're looking for information about "Visual Studio 2005 Team Edition for Database Professionals". Ah what a great name guys.....</p>
