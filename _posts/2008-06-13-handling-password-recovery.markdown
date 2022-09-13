---
layout: post
title: "Handling Password Recovery"
date: 2008-06-13 16:36:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Orcs Goblins  and .NET"]
alias: ["/post/Handling-Password-Recovery", "/post/handling-password-recovery"]
---
<!-- more -->
{% include imported_disclaimer.html %}
<p>I recently answered a blog post about how to handle password recovery in ASP.NET. My first thoughts when I read this questions are along the lines of, "Ah! Don't recover passwords!"</p>
<p>With any authentication system it is important to remember this one thing <strong>passwords should always be hashed</strong>. I don't care who you are or what system you're using, you should never ever have passwords stored in your system which are not at least encrypted in some format. In ASP.NET you want to use hashing. Being able to "recover" a password implies that the password is in a form that you could make it user-readable.</p>
<p>This is bad since it means that if someone managed to obtain your password data they could potentially obtain people's passwords. Considering that lots of users will use the same password in multiple places, that could be very bad.</p>
<p>What you need to do instead of recovering a password is to reset a user's password. They can then log in using the new password and change it to the one they want. This allows you to keep their password secure and to still allow them to recover from the issue. It just makes it a little bit more complicated for the user, but having the extra security is by far worth it. Most users will agree with you on this.</p>
<p>As a user I am quite upset when a site is able to "recover" my password. I am annoyed by the password policies of quite a few sites on the Internet. I've had sites limit the length of my passwords, limit the types of characters I may use, and many other sometimes asinine things.</p>
<p>Just always use password resets. It just makes things a little bit safer for your users. They'll be thanking you for it even if they don't actually express it to you.</p>
<p>Here you can read about <a href="http://quickstarts.asp.net/QuickStartv20/aspnet/doc/ctrlref/login/passwordrecovery.aspx" target="_blank">ASP.NET Password Recovery</a>. I just recommend you use hashed passwords and only allow password reset and not password retrieval.</p>
