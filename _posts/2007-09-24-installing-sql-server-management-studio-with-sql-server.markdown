---
layout: post
title: "Installing SQL Server Management Studio with SQL Server"
date: 2007-09-24 20:31:00 -0400
comments: true
published: true
categories: ["Archive"]
tags: ["Blog"]
permalink: "/post/Installing-SQL-Server-Management-Studio-with-SQL-Server/"
---
<!-- more -->



<p><strong>Update (24 March 2008):</strong> <a href="http://aspadvice.com/blogs/ssmith/archive/2008/03/21/SQL-2005-Tools-Install-Experience-is-the-suck.aspx">Steve Smith found a more reliable solution to install the SQL Server Client Tools</a>. Once in the tools folder open the setup folder and in there is a SqlRun_Tools.msi file. If you run that it should actually install SSMS.</p>
<p>When I recently installed SQL Server 2005 and SQL Server Management Studio on my computer it did not install SSMS or any of the other Client Tools. When running the installation of SQL Server 2005 I followed along with the instructions. I individually selected each component to install including the Client Tools for SQL Server. When the installation finished there was no SQL Server Management Studio.</p>
<p>Figuring this might be a difficult thing to Google for, I asked <a href="http://aspadvice.com/blogs/ssmith/">Steve Smith</a> if he knew how to get the client tools. He told me that just about the only way to get SSMS to install was to sacrifice a chicken and hope for luck, because there is something weird which has to be done in order to get the program to install.</p>
<p>Upon scouring the folders on the disc, I discovered that the default setup file is coming from a servers folder. I tried using the setup file from the&nbsp;tools folder. This should have worked, but I had a slight problem. Since I had told SQL Sever to install the client tools from the wrong setup file it now believed I had them installed already and would not install them.</p>
<p><a title="SQL Server 2005 Install Folders" href="http://www.flickr.com/photos/67369333@N00/1434709084/"><img src="http://static.flickr.com/1031/1434709084_8fa684f87a_m.jpg" border="0" alt="SQL Server 2005 Install Folders" /></a></p>
<p>Since the installation defaults to the Servers setup file, I never even saw the tools install. There was also no reason to even suspect one since the primary setup file claimed to be able to install the client tools.</p>
<p>I had to uninstall and reinstall SQL Server without the Client tools and then the setup file from the client tools would install SQL Server Management Studio. This was quite a pain, and I don't understand why the client tools are listed as options in a setup file which cannot install them. I think this is a bit crazy, but at least now when I install it I don't have this problem anymore.</p>
