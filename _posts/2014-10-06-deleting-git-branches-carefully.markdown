---
layout: post
title: "Deleting Git Branches Carefully"
date: 2014-10-06 14:00:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Blog"]
permalink: "/post/Deleting-Git-Branches-Carefully"
---
<!-- more -->



<p>I noticed someone recently using a “hard delete” in the git command line recently. I commented on it being brave, but it turns out that he didn’t realize there was a different way to delete a branch in git. In case anyone else is wondering the difference, here is a quick tip on it.</p> <p>In the git command line, you can use the “-D” parameter to delete a branch. It looks like this:</p><pre class="brush: ps;">git branch –D my-branch-name
</pre>
<p>This will delete the branch regardless of whether it’s been merged back in. This can be dangerous, since you may lose changes that you’ve not yet merged elsewhere.</p>
<p>If you want to be more careful with your branch deletion, you should use a lowercase “d” with the “-d” or “—delete” parameter. That would look like this:</p><pre class="brush: ps;">git branch –d my-branch-name
</pre>
<p>This will delete the branch only if you have merged the branch up already. This means that the branch’s changes should have been saved in the parent branch already, so it’s safe to delete. If you try this when it hasn’t been merged, you’ll received a message telling you that the branch was not deleted for this reason.</p>
<p>If you want to see the branches that still need to have their changes merged, you can do that using the following command:</p><pre class="brush: ps;">git branch --no-merged
</pre>
<p>If you want to see the branches that can safely be deleted, because their changes have already been merged upstream, you can use this command:</p><pre class="brush: ps;">git branch --merged
</pre>
<p>I hope you found these quick tips useful while you’re using git. If you’re new to git or GitHub, I recommend that you check out my Pluralsight course, <a href="http://www.pluralsight.com/courses/github-windows-developers" target="_blank">GitHub for Windows Developers</a>. The course takes an easy-to-follow approach to getting you set up using Git, GitHub, and GitHub for Windows.</p>
