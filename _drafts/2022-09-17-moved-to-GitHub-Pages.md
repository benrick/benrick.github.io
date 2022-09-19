---
layout: post
title: "Migrating Blog to Jekyll on GitHub Pages"
date: 2022-09-19 11:00:00 -0400
comments: true
published: true
categories: ["Tutorial", "Archive"]
tags: ["GitHub Pages", "BlogEngine.NET"]
permalink: "/post/Migrating-Blog-Jekyll-GitHub-Pages/"
---

I recently [moved my blog](/post/Moved-My-Site-to-GitHub-Pages/) (this one) from BlogEngine.NET to a Jekyll site on GitHub Pages. I tried to keep all of my posts working with the same URLs for the content. I didn't worry about the tags, categories, etc. pages remaining the same. I figured that no one linked to those anyway, so the redirects would only be important on the posts.

Hopefully this post will help you migrate an old site from any platform (not just BlogEngine.NET) to Jekyll on GitHub Pages.

## Exporting Existing Blog Content

Before we can create all of the posts on the new site, we'll need to export the posts from our existing site. For this, most sites have an export function. In BlogEngine.NET, you'll want to got to the Admin Dashboard by navigating to `/admin/` or clicking on `Dashboard` in the Admin widget.

![Adminstration Widget in BlogEngine.NET](/images/files/2022-posts/BlogMigration/AdministrationMenu.png)

From here, we need to open up `Settings -> Import export` then click on the `Export` button in the `Export` section of that page.

![Export Screen in BlogEngine.NET](/images/files/2022-posts/BlogMigration/ImportExportScreen.png)

When we click this button, the site will create a `BlogML.xml` and your browser will download it. That's an XML containing your posts, comments, metadata, etc. from your site.

<p class="message">I exported my comments, since I didn't care about preserving them. I did some googling and found that some people created tools to assist in moving this data to Disqus, but I haven't bothered with that yet.</p>

## Setting Up Jekyll Site on GitHub Pages

Now I needed a new GitHub repository to host the content for my site, so I created [benrick.github.io](https://github.com/benrick/benrick.github.io/) to host my site.

### Types of GitHub Pages sites

For GitHub Pages, you can set up `User`, `Organization`, or `Project` sites to be hosted by GitHub Pages.

I did a user site with repository name `benrick.github.io`, which followed the required repository name pattern of `[username].github.io` (will be the same as the address).

If I'd done a site for my `DevChatter` organization, it would've been `devchatter.github.io`, following the `[organization].github.io` pattern.

If I did a project site, it could've had any name, but would be hosted at `[username].github.io/[project-name]` or `[organization].github.io/[project-name]`. So if you're going to do this, be warned of the subfolder, which can be avoided with a custom domain (discussed below).

### Configuring the Repository as a GitHub Pages Site

Navigate to the `Settings` of the repository and click on the `Pages` in the `Code and automation` section of the sidebar navigation.

![Settings page showing Pages in sidebar]()



[Official GitHub Page Get Started Documentation](https://docs.github.com/en/pages/quickstart)

### Choosing and Customizing a Theme

Content about layouts and features here.

## Converting Blog Posts to Jekyll Markdown Posts

Content here

### Content Fixes

Content about fixing tags, categories, permalinks.

## Deploying and Verifying

Content here

## Setting up Custom Domain (Optional)

Content here and link to previous post.

I posted recently about [how to set up a custom domain from google domains for GitHub pages](/post/Custom-GitHub-Pages-Domain-with-Google-Domains/).
