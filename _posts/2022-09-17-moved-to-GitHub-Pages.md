---
layout: post
title: "Moved My Site to GitHub Pages"
date: 2022-09-17 17:00:00 -0400
comments: true
published: true
categories: ["Announcement", "Archive"]
tags: ["GitHub Pages"]
permalink: "/post/Moved-My-Site-to-GitHub-Pages/"
---

![Screen shot of the blog with its hydeout theme](/images/files/2022-posts/BlogScreenShot.png)

After more than a decade of maintaining a BlogEngine.NET site, I've finally bitten the bullet and moved to a static site. I'd meant to do this a few times in the past, having looked at a couple of C# static site generators, [Jekyll](https://jekyllrb.com/), [Wyam](https://wyam.io/), and a few others as well. I debated switching to WordPress as well, but that move wouldn't have gained me much, since I really wanted to move to a static site.

<p class="message">
  Hey chatter! I'll be posting another update soon that talks about how I migrated from BlogEngine.NET to Jekyll on GitHub Pages.
</p>

## Why a Static Site?

I chose to move to a static site for a few reasons. I'm tired of dealing with hosting a site, database, etc. for a blog. Considering that a blog is about the simplest set of content you can get, it seems overkill to maintain a SQL Database for that.

Now, I could've moved to a file-based data approach with my previous engine (it supports it), but I'd still be maintaining and paying to host a site. And to top it off, AspNet sites take some time to boot up on first hit, which I'd rather not deal with. I wanted to get rid of the backend-site.

## Why GitHub Pages with Jekyll?

It's free. It's easy. It's ubiquitous. I already use GitHub, and I'm proficient with GitHub Actions (a topic I will be discussing on future posts, videos, and streams), which I would use if I'm ever planning to make it more advanced than it is. Would also be useful for setting up a static site without Jekyll, since that's the one that GitHub pages uses.

### Breaking The Toughest Developer Puzzle Ever

More than a decade ago, a developer named Jeff Blankenburg created a game called **The Toughest Developer Puzzle Ever** (TDPE), and I participated in both iterations of the puzzle. For these, I created and hosted some of the puzzles in the sequences of Jeff's games. In order to not break my part of thegame, I made sure to maintain a blog that could still host the old pages.

See [Old TDPE Blog Post](/post/Have-you-tried-the-Toughest-Developer-Puzzle-Ever/) for more info.

As such, I used a C# blog engine, which meant that around that time, I moved my blog to BlogEngine.NET and it remained there until now.

## Theme Choice

I wanted to have a simple theme that didn't do too much yet. Maybe I'll grab a more advanced one at some point, but this has enough features for my initial move. I chose to use hydeout (is it still?), because it's a simple sidebar layout. I like the sidebar as it keeps it on-screen effectively for widescreen computers. I expect most of the traffic to a tech blog will be from laptops/desktops, not phones.

I've got basic support for tags, categories, and some other basics without too much bloat. What theme are you using for your site? If you're here in the future, does it still look the same?
