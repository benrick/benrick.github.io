---
layout: post
title: "Set Up Custom GitHub Pages Domain with Google Domains"
date: 2022-09-16 14:00:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Jekyll", "DNS", "CNAME", "Hosting", "Blogging", "GitHub Pages", "Google Domains", "Tutorials"]
permalink: "/post/Custom-GitHub-Pages-Domain-with-Google-Domains/"
---

![GitHub Pages Logo](/images/files/2022-posts/github-pages-logo.svg)

![Google Domains Logo](/images/files/2022-posts/google-domains-logo.svg)

## Intro

I recently set up my blog on GitHub pages, but I didn't want the `*.github.io` domain name. I have some of my domains in Google Domains, so I decided to set one of those up and write this tutorial for you after setting it up. Follow these steps and you too can have a custom domain.

## Step 0: Build a GitHub Pages Site and Own a Domain with Google Domains

Before you can set up the connection between [GitHub Pages](https://pages.github.com/) and [Google Domains](https://domains.google/) you'll need to have the site set up and the domain owned already.

Once you have those two things set up, come back here and you can set up your custom domain.

## Step 1: Configure DNS in Google Domains

Go to the [Google Domains Registrar](https://domains.google.com/registrar/), which should contain a list of domains you own there, and select the domain you want to configure.

![Google Domains Registrar List](/images/files/2022-posts/GDomainsRegistrar.png)

After clicking on the domain, you'll need to go to DNS in the left navigation.

![Google Domains Sidebar Navigation](/images/files/2022-posts/GDomainsSidebar.png)

### Set Up the DNS A Records

First, you'll want to set up the A Records to point your domain at the IP Addresses for GitHub Pages, so it looks like these:

![Google Domains Custom Records View](/images/files/2022-posts/GDomainsCustomRecordsView.png)

Click on `Manage Custom Records` to edit those on a screen like this:

![Google Domains Custom Records Edit](/images/files/2022-posts/GDomainsCustomRecordsEdit.png)

In that first record, leave the `Host name` blank, set the `Type` to "A", and the `Data` to the first IP Address. Then you click the `+ Add more to this record` until you've added all of these addresses.

- 185.199.108.153
- 185.199.109.153
- 185.199.110.153
- 185.199.111.153

You can check the [GitHub Pages Custom Domain Docs](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site#configuring-an-apex-domain) for the most up-to-date list of IP Addresses.

### Set Up the DNS CNAME Record

Next, while still on the `Manage Custom Records` scren, you'll want to set up the CNAME Record to point to the custom subdomain you have at google, mine is `benrick.github.io`. This will help if anyone tries going to the "www" version of your site.

Click on `Create new record` to add a new row to create the CNAME record like this:

![Google Domains Custom Records Edit](/images/files/2022-posts/GDomainsCustomRecordsEdit.png)

Just be sure that you set the `Host name` to "www", the `Type` to "CNAME" and the `Data` to you "*github.io" subdomain.

## Step 2: Configure the Custom Domain in GitHub Pages

Now that our records are in place, we can tell GitHub to check for them. As with all DNS changes, it can take some time to propogate, so you may have to wait until GitHub can verify.

From your GitHub repository, click on the "Settings" tab.

![GitHub Repository Top Nav Settings](/images/files/2022-posts/GitHubRepoTopNav.png)

From the Settings screen, you'll click on the "GitHub Pages" link in the sidebar navigation.

![GitHub Settings Side Nav](/images/files/2022-posts/GitHubRepoSettingsNav.png)

Now you'll want to change the Custom domain to your domain name that we just configured and save that change, which causes GitHub to run a check of the DNS settings.

![GitHub Pages Settings Custom Domain](/images/files/2022-posts/GitHubCustomDomainSetting.png)

After verification, the page will look like this:

![GitHub Pages Settings Custom Domain Verified](/images/files/2022-posts/GitHubCustomDomainSettingVerified.png)

<p class="message">
  Note here that I've enabled HTTPS for the site. While it's optional, enforcing HTTPS is a good idea!
</p>

## Step 3: Enjoy Your Site on its Custom Domain

Now you should be able to navigate to the site and see GitHub Pages site hosted using your custom domain name!
