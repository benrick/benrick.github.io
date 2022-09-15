---
layout: post
title: "SQL Server Client Tools Installation"
date: 2008-03-24 22:33:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Orcs Goblins  and .NET"]
permalink: "/post/SQL-Server-Client-Tools-Installation/"
---
<!-- more -->

<p>A while back <a href="/post/Installing-SQL-Server-Management-Studio-with-SQL-Server.aspx" target="_blank">I blogged about how to install sql server management studio</a>, and it got a reasonable amount of feedback. More recently, <a href="http://aspadvice.com/blogs/ssmith/" target="_blank">Steve Smith</a> posted a response to it where he highlights <a href="http://aspadvice.com/blogs/ssmith/archive/2008/03/21/SQL-2005-Tools-Install-Experience-is-the-suck.aspx" target="_blank">a better way of installing Management Studio</a>. The method I outlined doesn't seem to work in every instance, so in his response Steve supplied a method which works more often.</p>
<p><strong>The Solution: </strong>Run the SqlRun_Tools.msi file found in this folder.</p>
<p><strong>{drive}\ENGLISH\SQL2005\DEVELOPER\SQL Server x86\Tools\Setup\SqlRun_Tools.msi</strong></p>
<p><strong>{drive}\ENGLISH\SQL2005\DEVELOPER\SQL Server x64\Tools\Setup\SqlRun_Tools.msi</strong></p>
<p>Choose the top one for 32-bit systems and the bottom on for 64.</p>
<p>Lots of people keep UAC disabled on Windows, so they'll miss out on nice annoyances like the fact that this method requires you run the msi file as a local administrator. So as I am apt to do, I tried right clicking on it to choose the "Run As Administrator" context menu item. To my surprise it is not there! Below I've supplied the workaround I use in Vista for running as administrator when the context menu item is not present.</p>
<p><strong>One of many ways around running a program as administrator when the context menu item is not present.</strong></p>
<ol>
<li>In the start menu type "cmd".</li>
<li>When the dos prompt icon is the only remaining icon right click on it and run as administrator.</li>
<li>Copy the file location of the file you wish to run.</li>
<li>Paste the location into the command prompt window.</li>
<li>Click enter.</li>
<li>Watch the program begin with administrator privileges. </li>
<li>Celebrate and enjoy!</li>
</ol>
<p><strong>Update (9/9/2008):</strong> If the software claims that you have nothing to install when you run the <em>SqlRun_Tools.msi</em> then it means that installation has been borked. You will want to try running the <a href="http://download.microsoft.com/download/e/9/d/e9d80355-7ab4-45b8-80e8-983a48d5e1bd/msicuu2.exe">Microsoft Installation Cleanup Utility</a>. It will remove the client tools that SqlServer thinks are there, and it will then let you install them.</p>
