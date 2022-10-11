---
layout: post
title: "Change Local SQL Server Used By Visual Studio"
date: 2009-01-08 11:06:00 -0500
comments: true
published: true
categories: ["Archive"]
tags: ["Visual Studio", "MSSQL"]
permalink: "/post/Change-Local-SQL-Server-Used-By-Visual-Studio/"
---

<p>A while back I ran into a problem when setting up SQL Server on a computer and using it along with a database project in Visual Studio. It isn&rsquo;t really a big deal, but I needed to change which locally installed instance of SQL Server I was using by default with Visual Studio. Since I blogged about this previously it is a very nice reference for where to find that setting should the need to change it arise again.</p>
<p>Today I just sat down at a computer which had Visual Studio pointing to a SQL Express instance. Yesterday I installed SQL Server on the computer, so I went to change to the new SQL Server instance. What was my first step? I Googled for my blog post I&rsquo;d previously written, because I knew it had nice screen shots to show me exactly what I was looking for.</p>
<p>I simply searched for, &ldquo;change database Brendan Enrick&rdquo;. The top hit on Google was my previous post explaining <a href="http://aspadvice.com/blogs/name/archive/2008/04/02/Change-SQL-Server-Instance-for-Visual-Studio-Database-Project.aspx" target="_blank">how to change the SQL Server Instance for a Visual Studio Database Project</a>. As I mention in that post, I expected the setting to be DB Project specific not VS specific. Now I know better, and I just use the blog post for a quick solution.</p>
<p>Step one is to go to the <em>Tools</em> menu in Visual Studio and choose <em>Options&hellip;</em></p>
<p><img style="border-right: 0px; border-top: 0px; display: inline; margin-left: 0px; border-left: 0px; margin-right: 0px; border-bottom: 0px" title="Change SQL Server Instance Menu Selection" src="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/ChangeLocalSQLServerUsedByVisualStudio_9C54/ChangeSQlServerInstanceMenuSelection_5.jpg" border="0" alt="Change SQL Server Instance Menu Selection" width="342" height="503" /></p>
<p>Now that the <em>Options</em> windows is open in the left side navigation tree select <em>Database Tools</em> and then <em>Design-time Validation Database</em>. Once that screen is visible there is a text box to change the <em>SQL Server Instance Name</em>. Set that to the name of your desired SQL Server Instance. In my case the default one, so I erased the existing value.</p>
<p><img style="border-right: 0px; border-top: 0px; display: inline; border-left: 0px; border-bottom: 0px" title="Change SQL ServerInstance Options Change" src="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/ChangeLocalSQLServerUsedByVisualStudio_9C54/ChangeSQLServerInstanceOptionsChange_3.jpg" border="0" alt="Change SQL ServerInstance Options Change" width="504" height="296" /></p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>This is one of the big reasons why I am a strong believer in blogging. It is a quick easy way to get this information out for others to use. Posts like this often get a few comments of thanks from people they helped. If helping others in the development community is not enough of a reason, you also always have a record to help you if you run into the same problem again.</p>
