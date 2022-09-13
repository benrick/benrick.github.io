---
layout: post
title: "Flags Over Objects"
date: 2014-07-02 10:00:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Blog"]
alias: ["/post/Flags-Over-Objects", "/post/flags-over-objects"]
---
<!-- more -->

<p>If you didn’t notice it, our “flag” month was the same month as <em>Independence Day</em> in the United States. We celebrate that day with flags, fireworks, and a lot of cookouts. Notice anything in the picture? Yep. We’re missing the fireworks. Anyway, the topic of <a href="http://deviq.com/flags-over-objects" target="_blank">Flags Over Objects</a> is an important one.</p>  <p>Flags Over Objects is the Software Craftsmanship Calendar’s anti-pattern topic in July 2014. As a developer, I am sure that you’ve come across code where boolean values (flags) were used far too much. This is often a misuse of state. Plenty of times there is a better, simpler way of handling the state of objects.</p>  <p><a href="http://brendan.enrick.com/image.axd?picture=Flags_Over_Objects_July_2014.png"><img title="Flags_Over_Objects_July_2014" style="border-left-width: 0px; border-right-width: 0px; border-bottom-width: 0px; display: inline; border-top-width: 0px" border="0" alt="Flags_Over_Objects_July_2014" src="http://brendan.enrick.com/image.axd?picture=Flags_Over_Objects_July_2014_thumb.png" width="350" height="350" /></a> </p>  <p>In this image, you might notice (looking carefully) a few obvious (and common) issues with using flags. First, you’ve got a whole list of checkboxes even though some of those can only ever be one at a time. You might also notice that there are a lot of repeats of the same checkbox.</p>  <p>Are you using this anti-pattern anywhere?</p>
