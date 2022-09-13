---
layout: post
title: "Quick Silverlight Tip: Looking at the code"
date: 2010-02-01 14:18:00 -0500
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Blog"]
alias: ["/post/Quick-Silverlight-Tip-Looking-at-the-code", "/post/quick-silverlight-tip-looking-at-the-code"]
---
<!-- more -->
{% include imported_disclaimer.html %}
<p>Silverlight is a great technology, and one thing that really makes it a treat to work with is the ease with which one can access the code inside the XAP file. Yes, this means that someone can look at your code,&nbsp; SO DON&rsquo;T PUT ANYTHING SECURE IN THERE! I took Jeff Blankenburg&rsquo;s <a href="http://jeffblankenburg.com/2010/01/click-button-contest.aspx" target="_blank">Click the Button contest</a>.</p>
<p>So for a while I though Jeff had tricked me on that puzzle until I opened up the XAP file and looked at the source code. On the last page of the Silverlight you see this screen.</p>
<p><a href="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/QuickSilverlightTipLookingatthecode_C8B6/Level%2012_2.png"><img style="border-bottom: 0px; border-left: 0px; display: inline; border-top: 0px; border-right: 0px" title="Level 12" src="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/QuickSilverlightTipLookingatthecode_C8B6/Level%2012_thumb.png" border="0" alt="Level 12" width="404" height="187" /></a></p>
<p>So what&rsquo;s the big deal? Well, the level before it was titled &ldquo;Level 10&rdquo;, so I figured Jeff was trying to pull a fast one and there was more to this seemingly innocent page. So I tried to find how to get beyond this level 12 to the real one. I eventually took the smart route, and I opened <a href="http://www.red-gate.com/products/reflector/" target="_blank">.NET Reflector</a> and pointed it at the DLL file for the contest.</p>
<p><em>How did I do that you ask? Here are some quick steps for looking at the source code of a Silverlight application.</em></p>
<p><strong>Step 1:</strong> Download the .xap file. View the source of the HTML page or look at the NET tab in FireBug to get the .xap file and download it.</p>
<p><strong>Step 2: </strong>Rename the file to .zip and open it. Yes, a .xap is really a .zip neat huh?</p>
<p><strong>Step 3: </strong>Unzip the file and find the dll you&rsquo;re looking for. In my case it is called &ldquo;ClickTheButton.dll&rdquo;</p>
<p><strong>Step 4:</strong> Open up .NET Reflector and open up that dll file.</p>
<p><a href="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/QuickSilverlightTipLookingatthecode_C8B6/NewDllInReflector_2.png"><img style="border-bottom: 0px; border-left: 0px; display: inline; border-top: 0px; border-right: 0px" title="NewDllInReflector" src="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/QuickSilverlightTipLookingatthecode_C8B6/NewDllInReflector_thumb.png" border="0" alt="NewDllInReflector" width="372" height="576" /></a></p>
<p><strong>Step 5:</strong> After examining the dll you&rsquo;ll be able to see all of the code. In this case I can see that Jeff actually has 13 levels he created for this application.</p>
<p>You now have a choice to make. You can ask Jeff Blankenburg what happened to the other puzzles or just go and take a look at the code and see which levels are missing.</p>
