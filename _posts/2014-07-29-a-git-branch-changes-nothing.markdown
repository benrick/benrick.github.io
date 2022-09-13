---
layout: post
title: "A Git Branch Changes Nothing"
date: 2014-07-29 18:00:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Blog"]
alias: ["/post/a-git-branch-changes-nothing"]
---
<!-- more -->
{% include imported_disclaimer.html %}
<p>I'm serious. If you create a new branch in git, you didn't really do much of anything. All you did was make a pointer. There is no copying of the files. No additional changesets. When you checkout the branch you just created, you still didn't really do anything. It just changes which branch you’re on. The files don’t change at all. That's because git does not need to change the source code at all in order to deal with this new branch.</p> <p>When you start changing the code, however, you'll be adding new commits that are in that branch. The branch itself isn't really a thing though, since git effectively just makes a linked list of your changesets.</p> <p><a href="http://brendan.enrick.com/image.axd?picture=NetworkGraph.png"><img title="NetworkGraph" style="border-left-width: 0px; max-width: 100%; border-right-width: 0px; background-image: none; border-bottom-width: 0px; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-top-width: 0px" border="0" alt="NetworkGraph" src="http://brendan.enrick.com/image.axd?picture=NetworkGraph_thumb.png"></a></p> <p>In the example shown here, notice that the blue line for “feature-xyz” does not have a dot until it’s first commit. That is because the branch starts, and it’s just a link pointing nowhere. Once there is a commit, there is some significance, but the branch itself is nothing. Git is primarily just a tree made of these links. This simple example illustrates some basic branching and merging.</p> <p>I hope this little bit of info about git makes using it easier. If you want to learn more about using GitHub, please check out my <a href="http://pluralsight.com/training/Courses/TableOfContents/github-windows-developers" target="_blank">Pluralsight course on GitHub</a>.</p>
