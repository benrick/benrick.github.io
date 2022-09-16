---
layout: post
title: "Boy Scout Rule"
date: 2012-07-11 11:00:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Software Craftsmanship", "Calendar Topic"]
permalink: "/post/Boy-Scout-Rule/"
---
<!-- more -->



<p>When and how much time to spend refactoring out code is one of the best questions that a budding software craftsman will ask. It&rsquo;s one I&rsquo;ve asked and answered many times. There isn&rsquo;t one specific answer that is better than all of the others. It always depends on your personal preference, the restrictions of you client, company, or team, your code base, your language, your version control, and many other issues.</p>
<p>One rule, which is the one that I follow and encourage others to follow, is the Boy Scout Rule. It&rsquo;s based on the &ldquo;leave the campsite better than you found it&rdquo; idea. It&rsquo;s often said to be a line related to the scouts, but it seems to work well for code also.</p>
<p>If you have some old code that needs refactoring, I would guess it&rsquo;s not tested. Since it&rsquo;s not tested, you run the risk of creating bugs <em>even if you&rsquo;re testing it while refactoring.</em> Some small changes will need to be made in order to test the code. You could miss <em>something</em>. That makes it dangerous. This is why you want to keep your refactoring to small pieces at a time. When and where you refactor are the next questions.</p>
<p>The Boy Scout Rule answers these questions nicely. You want to refactor the code you&rsquo;re working on now. It&rsquo;s fresh in your mind. You know how it&rsquo;s supposed to work since you&rsquo;re in there making changes now. It obviously is a volatile place, which should be cleaned up. You&rsquo;re in there changing it now aren&rsquo;t you?</p>
<p>Plus your current change might make things worse if you don&rsquo;t do a bit of refactoring first!</p>
<p>The 2011 NimblePros Software Craftsmanship Calendar featured the Boy Scout Rule in the month of July, so for the rest of July, try to do small pieces of refactoring as you go into parts of a legacy codebase. Rewrite some code, write a test if you can, update an outdated comment (if you don&rsquo;t just remove it), or even just write a better variable name.</p>
<p>It&rsquo;s all about incremental improvements. The agile community should be loving this rule, since it is all about incremental changes and improvements.</p>
<p><img style="background-image: none; border-bottom: 0px; border-left: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top: 0px; border-right: 0px; padding-top: 0px" title="Boy Scout Rule" src="/images/files/BoyScoutRule.png" border="0" alt="Boy Scout Rule" width="481" height="480" /></p>
<p>Enjoy the rest of July! Don&rsquo;t forget that you should also be avoiding <a href="/post/Feature-Creep.aspx">Feature Creep</a>.</p>
