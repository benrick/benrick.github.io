---
layout: post
title: "Moved My Site to GitHub Pages"
date: 2022-09-17 12:00:00 -0400
comments: true
published: true
categories: ["Announcement", "Archive"]
tags: ["GitHub Pages"]
permalink: "/post/Moved-My-Site-to-GitHub-Pages/"
---

After more than a decade of maintaining a BlogEngine.NET site, I've finally bitten the bullet and moved to a static site. I'd meant to do this a few times in the past, having looked at a couple of C# static site generators, Jekyll, and a few others as well. I debated switching to WordPress as well, but that move wouldn't have gained me much.

## Why a Static Site?

I chose to move to a static site for a few reasons. I'm tired of dealing with hosting a site, database, etc. for a blog. Considering that a blog is about the simplest set of content you can get, it seems overkill to maintain a SQL Database for that.

Now, I could've moved to a file-based approach with my previous engine, but I'd still be maintaining and paying to host a site. And to top it off, AspNet sites take some time to boot up on first hit, which I'd rather not deal with.

## Why GitHub Pages?

It's free. It's easy. It's ubiquitous. I already use GitHub, and am proficient with GitHub Actions if I'm ever planning to make it more advanced than it is.

### Breaking The Toughest Developer Puzzle Ever

More than a decade ago, a developer named Jeff Blankenburg created a game called **The Toughest Developer Puzzle Ever** (TDPE), and I participated in both iterations of the puzzle. For these, I created and hosted some of the puzzles in the sequences of Jeff's games. In order to not break my part of thegame, I made sure to maintain a blog that could still host the old pages.

See [Old TDPE Blog Post](/post/Have-you-tried-the-Toughest-Developer-Puzzle-Ever/) for more info.

As such, I used a C# blog engine, which meant that around that time, I moved my blog to BlogEngine.NET and it remained there until now.
