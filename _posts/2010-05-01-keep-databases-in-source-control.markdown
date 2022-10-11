---
layout: post
title: "Keep Databases in Source Control"
date: 2010-05-01 10:27:00 -0400
comments: true
published: true
categories: ["Archive"]
tags: ["Database Change Management", "Databases", "Source Control"]
permalink: "/post/Keep-Databases-in-Source-Control/"
---

<p>Well, sort of. Your database can be rather large, so you probably don&rsquo;t want to actually have the database file in source control. I do think you should have your database in source control, but really just your schema. Remember in my post about <a href="/post/keep-binaries-in-source-control/" target="_blank">keeping your binaries in source control</a> I mentioned that it is important to be able to go back to any point in time for your application. <em>This means the database will need to match as well.</em> How can we allow ourselves to do that? Keep databases in source control.</p>
<p>We want to be storing the subset of SQL usually defined as the Data Definition Language. These are all of the statements that create tables, define columns, create indexes, and make any alterations to our database schema. There are plenty of ways to store these. In fact I recommend after reading this post that you attend a local user group and offer this topic as a discussion for an open space. We&rsquo;ve done this topic at <a href="http://hudsonsc.com/" target="_blank">HudsonSC</a> and you get to find out a lot about what solutions other teams are using and why they&rsquo;re using them.</p>
<h3>Why store the database in source control?</h3>
<p>We get a few advantages here. This is not an exhaustive list, but it does include some good reasons for following this practice.</p>
<ul>
<li>You can set up your project on any computer and have a local database to test against.</li>
<li>Always be able to rebuild your database if anything happens to it.</li>
<li>Go back to any point in time and be able to create the database.</li>
<li>Incrementally change things and be able to see what changes have been made at any point.</li>
</ul>
<h3>How can I store my database in source control?</h3>
<p>There are plenty of ways in which you can store your database in source control. I&rsquo;ve used a few different techniques for doing this. There are some tools which can help you do this. Keep in mind that you can build your own as well. They&rsquo;re not very difficult to create.</p>
<p>I have used Visual Studio Database projects before. These are nice because they&rsquo;re a full package for handling the changes. This is the heavyweight approach to managing your database changes. This keeps each table, index, key, view, stored procedure, etc. as its own file. This built-in Visual Studio system allows you to update the project and use the project to update database.</p>
<p>The lightweight approach is to make each change using a sql script. You can write the alter, create, and drop statements by hand and store each one in a file. This approach makes it harder to see how each table has changed over time, but gives a better view of what changes were made at what points in time. In order to deploy the database updates you&rsquo;ll either need to write your own system or use a tool like <a href="http://code.google.com/p/tarantino/" target="_blank">Tarantino</a> to keep track of the changes.</p>
<p>There are of course other tools for handling this situation. What tools are you using for managing your database?</p>
<h3>Other considerations</h3>
<p>You will probably also want to have some code which can fill your test database with data to be used for locally running your application. I recommend having this code be compiled code (not SQL scripts). The reason for this is so that you can have the compiler assist you in ensuring that the scripts aren&rsquo;t out of date. You also want this to be part of your build process, so that no one can forget to update it. It should be run by your <a href="/post/2009/06/11/Everyone-Should-Have-a-Continuous-Integration-Server.aspx" target="_blank">continuous integration server</a>, so that the build will break if there are any issues.</p>
<p>This will also make updating your production database a lot easier since you will have stored scripts which define exactly which operations need to be performed in order to update your database according to the changes you&rsquo;ve made.</p>
