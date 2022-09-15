---
layout: post
title: "Deleting a Remote Git Branch"
date: 2014-10-08 14:00:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Blog"]
permalink: "/post/Deleting-a-Remote-Git-Branch/"
---
<!-- more -->

<p>Another bit of git command line that a lot of people struggle to remember is the syntax to delete a remote branch. If you read my post from a couple of days ago, I mentioned a couple of things about <a href="http://brendan.enrick.com/post/Deleting-Git-Branches-Carefully" target="_blank">deleting git branches</a>. That’s how you delete them locally. If you want to push that deletion up to the remote repository as well, you need to take one additional step.</p> <p>The command I use to delete remote branches is this:</p><pre class="brush: ps;">git push origin :my-branch-name
</pre>
<p>It’s that “:” that tells it to delete the branch. Yes, it may seem confusing, but there is a reason for it. I’ll explain below for those who are interested in learning more.</p>
<p>Here is a slightly easier syntax, but I don’t like typing the additional characters.</p><pre class="brush: ps;">git push origin --delete my-branch-name
</pre>
<p>Feel free to use this syntax, it’s newer, but you most likely have support for it. It’s been out for years now. </p>
<p>Here is the reason (other than its being shorter) that I like the first syntax better.</p>
<p>If you want to push our a git branch, you use this command:</p><pre class="brush: ps;">git push origin my-branch-name
</pre>
<p>If you wanted it to have a different name remotely than it has locally, you would do this:</p><pre class="brush: ps;">git push origin my-local-name:my-remote-name
</pre>
<p>Which means that if you wanted to push “nothing” over the remote branch with that name you would do this:</p><pre class="brush: ps;">git push origin :my-remote-name
</pre>
<p>Notice how the command is pushing empty over that branch, which is then interpreted as a “delete” by git. That’s how I make sense of it, plus this is a neat little bit of info about the command.</p>
<p>I hope this helps people adopt and use git more easily. If you’re new to git or GitHub, I recommend that you check out my Pluralsight course, <a href="http://www.pluralsight.com/courses/github-windows-developers" target="_blank">GitHub for Windows Developers</a>. The course takes an easy-to-follow approach to getting you set up using Git, GitHub, and GitHub for Windows.</p>
