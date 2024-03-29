---
layout: post
title: "IIS 7 Not Serving Static Files"
date: 2011-02-22 09:59:00 -0500
comments: true
published: true
categories: ["Archive"]
tags: ["IIS"]
permalink: "/post/IIS-7-Not-Serving-Static-Files/"
---
<!-- more -->



<p>I learned this potentially very useful bit of information from <a href="http://weblogs.asp.net/owscott/" target="_blank">Scott Forsyth</a> recently. As you may know, IIS 7 is modular, which allows for a great deal of control and customization of an IIS installation. There are a lot of other great benefits also. Web servers are great tools that allow us to put our content on the web. One of the most powerful things is their support for creating dynamic sites through different programming frameworks and languages. We sometimes take for granted our having static content in our web server. The static content is all of the common content on a site, which is not dynamic. In general this means our htm, html, and image files.</p>  <p>If you’re ever not serving that content then you should make sure that your IIS installation is set up to serve that content using these steps.</p>  <p><strong>Open up the control panel and click on the Programs category.</strong></p>  <p><a href="/images/files/ControlPanel.png"><img style="background-image: none; border-bottom: 0px; border-left: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top: 0px; border-right: 0px; padding-top: 0px" title="ControlPanel" border="0" alt="ControlPanel" src="/images/files/ControlPanel_thumb.png" width="480" height="340"></a></p>    <p><strong>Click on “Turn Windows features on or off” in the Programs and features section.</strong></p>  <p><a href="/images/files/Programs.png"><img style="background-image: none; border-bottom: 0px; border-left: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top: 0px; border-right: 0px; padding-top: 0px" title="Programs" border="0" alt="Programs" src="/images/files/Programs_thumb.png" width="480" height="340"></a></p>  <p><strong>Expand in the tree view in this order:</strong> <em>Internet Information Services</em><strong>,</strong> <em>World Wide Web Services</em><strong>, </strong><em>Common HTTP Features</em><strong>. Then make sure that</strong> <em>Static Content</em> <strong>is checked.</strong></p>  <p><a href="/images/files/WindowsFeatures.png"><img style="background-image: none; border-bottom: 0px; border-left: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top: 0px; border-right: 0px; padding-top: 0px" title="WindowsFeatures" border="0" alt="WindowsFeatures" src="/images/files/WindowsFeatures_thumb.png" width="360" height="412"></a></p>  <p>If that was unchecked and you checked it and clicked OK, then you should be all set and serving static files like images and html pages in your web site.</p>  <p>Not really sure why someone would want to turn that off, but at least it is easy to turn that setting back on.</p>
