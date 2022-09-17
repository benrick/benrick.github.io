---
layout: post
title: "Security Policies - Code Audits #7"
date: 2012-07-10 10:00:00 -0400
comments: true
published: true
categories: ["blog", "Archive"]
tags: ["Code Audits", "DaysOfCodeAudits"]
permalink: "/post/Security-Policies-Code-Audits-7/"
---
<!-- more -->



<p>I think we&rsquo;ve all heard about the great security policies that companies implement.</p>
<p>Companies want you changing your password every other day, without repeating any passwords you&rsquo;ve ever used, without using any characters from your first name or last name, without having any numbers associated with your address, phone number, birth date, the current year, or your age, and they want your password to be exactly 12 characters.</p>
<p>All of these rules are really funny. I don&rsquo;t think I need to tell too many people that there are <a href="http://xkcd.com/936/" target="_blank">better</a> ways of creating <a href="http://www.codinghorror.com/blog/2005/08/passphrase-evangelism.html" target="_blank">passwords</a>.</p>
<p>All of that aside, those rules are kind of interesting. I use a lot of different passwords. I change the important ones. I don&rsquo;t change the unimportant ones.</p>
<h3>The Bad</h3>
<p>When companies implement these policies, they like to have software in place to enforce the policies. Now is a great time to discuss how not to manage these policies.</p>
<p>In this instance the company requires that passwords be changed every 2 months. The passwords cannot contain more than 2 consecutive characters from the person&rsquo;s first and last name (challenging to avoid as a user creating a password). You cannot use any of your last 3 passwords.</p>
<p>I was going to be rewriting this logic in a new system. I asked a few questions about this. One important questions is, if the password needs to be updated if the person&rsquo;s name changes. For example they could have gotten married and may not be violating the password not containing consecutive name characters issue. Since I can&rsquo;t find out what their password is in code, I have to just make them change the password.</p>
<p>This company obviously cares about securing this information since it&rsquo;s implementing this password policy.</p>
<p>The application is using salted, hashed passwords when storing them in the database. That&rsquo;s good.</p>
<p>I later noticed how the existing system handled password history. Clear text passwords stored with the username all in a table in the database. Every single password every user had ever used on the site. This is a scary pile of passwords that likely get used all over the Internet by these users. It even included the current password being used by that user.</p>
<h3>The Better</h3>
<p>These should not be stored this way! If you have to keep passwords around, keep the hash only. Also, get a new salt with each new password. Treat these as passwords (they are!) Don&rsquo;t be foolishly insecure with this stuff. If someone accessed that database, they would have usernames and passwords for people to try all over the Internet. That would be a huge disaster.</p>
<p>If you have to keep that kind of information around, at least don&rsquo;t have it in clear text. It would also be a good idea to limit the information that is there by removing the old passwords that are no longer relevant. Since they only care about the last 3 in the history, there is no reason to keep any more than that. Remove the old ones.</p>
<p>To be honest, I also don&rsquo;t think that those types of password policies are all that secure anyway. I am sure that there is a weak link somewhere in the human element that would render the policy useless anyway.</p>
<h3>More Code Audit Nuggets</h3>
<p>Keep watching for more interesting nuggets of stuff that I&rsquo;ve seen in codebases.</p>
