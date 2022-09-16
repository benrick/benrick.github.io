---
layout: post
title: "Upgrading to XtraReports version 7.3.6.0"
date: 2008-02-28 14:40:00 -0500
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Blog"]
permalink: "/post/Upgrading-to-XtraReports-version-7360/"
---
<!-- more -->



<p>A few weeks ago I upgraded a site using XtraReports to a newer version. I upgraded from 7.1.3.0 to 7.3.6.0 (not a major revision update) and the results were simply amazing. Looking at the version number I would assume that no major changes were made, so upgrading the software should be quite simple right? No, there were plenty of breaking changes for me to update. This is not to say that there is anything wrong with the new version. In fact I love the new version of this product. Why? Because they did change the old crappy implementation of their reporting.</p>
<p>As with most reports it is common to filter the data which will be placed into the report. With the old version of these reports it was <em><strong><span style="text-decoration: underline;">fun</span></strong></em>. Lets just say that the reports previously rendered inside of iframes, so if you tried to use paging in the report it would not be a postback. You'll lose your filter values if you page. OK so you need to have your filtering work whether it is a postback or not, so you need to store it in some form of saved state that will work. Basically you end up storing the values in Session. Yeah. A bit hacky huh? Well, when we upgraded to the new version all of a sudden all of our reports were broken. This is because..... THEY GOT RID OF THE IFRAME!!!! &lt;cue the celebration music&gt; So I happily did a bunch of work removing all of the hacked together code that made the filtering work. Now the code is clear and easy to follow. It is far less error prone.</p>
<p>I like the reports. They're very nice controls, but that previous implementation was a bit crazy. I no longer have my huge complaint about XtraReports. They're now very easy to work with. So if you're using an old version of XtraReports and have seen the problem I mention above, go get yourself the new version of XtraReports even after the extra work you need to do you'll be quite happy.</p>
<p>Good day to you.</p>
