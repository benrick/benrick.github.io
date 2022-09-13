---
layout: post
title: "Agile Story Estimation"
date: 2010-04-23 11:29:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Blog", "Blog"]
alias: ["/post/Agile-Story-Estimation", "/post/agile-story-estimation"]
---
<!-- more -->

<p>One challenging part of software development is estimating the amount of time that tasks will take. Why is this a challenge? There are plenty of reasons: sometimes you&rsquo;re dealing with legacy code, sometimes there are a great deal of unknowns, and sometimes you aren&rsquo;t doing the whole story and can&rsquo;t estimate the other work. There are plenty of other reasons why estimating stories is difficult, so how do you resolve the difficulties and get things estimated.</p>
<h3>&nbsp;</h3>
<h3>Improving Estimates</h3>
<p>I find it is best to bring the whole group together to make estimates. With a group, you&rsquo;re less likely to forget about different aspects of the project. You&rsquo;ll have everyone there who will be doing the tasks. Someone there may know more about the legacy system or a certain part of it than you do.The group should help prevent you from making any unrealistic estimates.</p>
<p>Another great way of improving your story estimates is to do the estimating shortly before you&rsquo;re going to be doing the work. The best estimates you can make can only be done immediately before doing the task. Any earlier and you don&rsquo;t know exactly how the system will be architected. Estimate any earlier and the system may have become easier or harder to change before you start the task.</p>
<p>To help build group consensus on the estimates you want to limit the number of options available. With too many numbers it will be very hard to get everyone to agree. You also want to have less options as the numbers get larger. The reason being that larger estimates are less accurate anyway, so you really just want a magnitude for the estimate. Is this a day-long task? More?</p>
<p>Find some nice system to limit the numbers. A great way that I&rsquo;ve seen used in the past is Fibonacci numbers only.</p>
<blockquote>
<p>1, 2, 3, 5, 8, 13, 21&hellip;</p>
</blockquote>
<p>That set allows for some accuracy at the bottom and some good general choices up higher. 8 is great because it is a full-day.</p>
<p>My favorite set of numbers for estimating is using the powers of 2.</p>
<blockquote>
<p>1, 2, 4, 8, 16, 32&hellip;</p>
</blockquote>
<p>I&rsquo;ll explain later why I like this set of numbers.</p>
<p>Another easy set to use is Prime Numbers (with 1 included).</p>
<blockquote>
<p>1, 2, 3, 5, 7, 11, 13</p>
</blockquote>
<p>Whatever set you choose make sure that the group knows which ones you&rsquo;re using and stick with it.</p>
<h3>Implementing Estimates</h3>
<p>Once you select your strategy for estimating you&rsquo;ll need to implement it. Estimating should be done close to when the task will be done, so I recommend estimating on each Monday all of the stories for the week.</p>
<p>Bring everyone together and make sure they understand how the estimating will be done. You want to start by reading one of the stories. Let the team ask any questions about the story. Once everyone understands the task you get to estimate.</p>
<p>Make sure that everyone selects their estimate secretly this is important so that no one&rsquo;s estimate is influenced by others&rsquo; estimates. I&rsquo;ve seen a few interesting ways of doing this.</p>
<p>The cheapest approach is to have each person hold up a number of fingers equal to his estimate, and then all estimators reveal their estimates at the same time. This is kind of like a game of rock-paper-scissors. We can call this approach Rock-Paper-Estimate.</p>
<p>Another easy approach is to have everyone write down the number and reveal at the same time. You could use paper for this or little whiteboards.</p>
<p>A very cool trick that was brought to my attention recently came from someone handing me a deck of cards from the Visual Studio 2010 launch event in Las Vegas. <a href="http://en.wikipedia.org/wiki/Planning_poker" target="_blank">Planning Poker</a>. It is basically a deck of cards with estimates on the cards. There are 4 different colors, so 4 people could be estimating at any given time with a single deck.</p>
<p><a href="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/AgileStoryEstimation_9853/IMG_0359.jpg"><img style="border: 0px none; display: inline;" title="IMG_0359" src="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/AgileStoryEstimation_9853/IMG_0359_thumb.jpg" border="0" alt="IMG_0359" width="400" /></a></p>
<p><a href="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/AgileStoryEstimation_9853/IMG_0360.jpg"><img style="border: 0px none; display: inline;" title="IMG_0360" src="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/AgileStoryEstimation_9853/IMG_0360_thumb.jpg" border="0" alt="IMG_0360" width="400" /></a></p>
<p>Whatever method you use, make sure you work for the group's agreement and try to keep things fast-paced.</p>
