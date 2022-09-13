---
layout: post
title: "My Team Server Headache"
date: 2006-09-22 17:02:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Orcs Goblins  and .NET"]
permalink: "/post/My-Team-Server-Headache"
---
<!-- more -->

<p>So yesterday I was able to spend a long time battling with team server. It seams that source controls likes to keep track of where your workspaces are itself. So on a computer I don&rsquo;t normally work on, I logged in. I set up work spaces on that machine, because Team Server didn&rsquo;t specify them for me. I needed to put the code in a public place, so I did. When I went back to my normal machine, I told the server I wanted to get latest. Wow was that a huge mistake.</p>
<p>Five to ten minutes, and a seemingly endless stream of error messages later, team server has moved half of all of my files to another location. It seems that it noticed from the other machine that I had moved my workspaces, so it tried to do the same on my work machine. All hell broke loose when it could not get all of the files moved correctly. As should be quite obvious, Visual Studio cannot build half projects.</p>
<p>The best part of this whole experience was the time it took to move EVERYTHING back to its original location so I could start working again. All I wanted was&nbsp;1 updated file. Never going to move workspaces again&hellip;..</p>
<p>Perhaps someone knows of some cool trick to stop that from happening. If you do I would appreciate knowing as well. Thanks.</p>
