---
layout: post
title: "Enabling Mixed Mode Authentication in SQL Server"
date: 2008-04-03 16:52:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Orcs Goblins  and .NET"]
permalink: "/post/Enabling-Mixed-Mode-Authentication-in-SQL-Server"
---
<!-- more -->

<p>I recently needed to enable Mixed Mode Authentication on a SQL Server instance, so I will demonstrate how to go about setting this up. It is a pretty easy process, but I figure I'll document it nicely here. Perhaps I will come back to this later to reference this. Who knows?</p>
<p>First you will need to connect to the SQL Server instance using SQL Server Management Studio.</p>
<p><img src="http://static.flickr.com/2231/2384726619_bc5ded628b.jpg" border="0" alt="SQLServerConnectWindow" /></p>
<p>Once you've connected to the SQL Server you will need to get to the properties window for the server. To do this you can right click on the SQL Server in the Object Explorer window and it will bring up a context menu.</p>
<p><img src="http://static.flickr.com/3235/2384726633_ca23b2fa9a.jpg" border="0" alt="SQLServerContextMenu" /></p>
<p>Now that you've got the properties window open, select the Security section and choose the SQL Server and Windows Authentication Mode radio button.</p>
<p><img src="http://static.flickr.com/2068/2385558414_8d85fa62cf.jpg" border="0" alt="SQLServerMixedModeAuth" /></p>
<p>After clicking OK, you will receive a message informing you of the need to restart the Server before the changes take affect.</p>
<p><img src="http://static.flickr.com/2372/2385558444_42a426b6a5.jpg" border="0" alt="SQLServerConfigMessage" /></p>
<p>Now just right click on the server in the object explorer again and select restart from the context menu and the services for the server will restart.</p>
<p><img src="http://static.flickr.com/3070/2385558472_2a59d81b63.jpg" border="0" alt="SQLServerRestartContext" /></p>
<p>Congratulations you're done.</p>
