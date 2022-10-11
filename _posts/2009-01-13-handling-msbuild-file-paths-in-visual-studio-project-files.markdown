---
layout: post
title: "Handling msbuild File Paths in Visual Studio Project Files"
date: 2009-01-13 10:47:00 -0500
comments: true
published: true
categories: ["Archive"]
tags: ["MSBuild", "Visual Studio"]
permalink: "/post/Handling-msbuild-File-Paths-in-Visual-Studio-Project-Files/"
---

<p>Yesterday, a co-worker of mine and I were working on a task which required that we work in the xml of a Visual Studio project file. We were setting up a target with an exec statement, and ran into a little annoyance. The file we were trying to execute was in a folder with a space in the name.</p>
<p>If we were typing this into a command prompt window it would be easy. We would simply wrap the statement in quotes. Working in the project file our brains sort of stopped working. We tried to find a way to escape the spaces in the file path. Instead of doing this in the end we used the xml encoding for a quote. We used <strong>&amp;quot;</strong> to wrap the path in quotes. Yipee everything worked!</p>
<p>Today we were doing some similar work, and ran into another problem in these files. We want our msbuild stuff to work with both 32-bit and 64-bit machines. The code we are calling is always 32-bit, so we need to use a different file path depending on which type of machine we are using. We found this post on stack overflow from a person who found a way to <a href="http://stackoverflow.com/questions/346175/use-32bit-program-files-directory-in-msbuild" target="_blank">specify the 32bit directory for program files in msbuild</a>. The post on there is asking for a better solution, so I will also ask people to provide a better solution.</p>
<p>This is how <a href="http://stackoverflow.com/users/33499/wimmel" target="_blank">Wimmel</a> solved the problem.</p>
<div>
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;"><span style="color: #0000ff">&lt;</span><span style="color: #800000">PropertyGroup</span><span style="color: #0000ff">&gt;</span>
  <span style="color: #0000ff">&lt;</span><span style="color: #800000">ProgramFiles32</span> 
    <span style="color: #ff0000">Condition</span><span style="color: #0000ff">="Exists('$(PROGRAMFILES) (x86)')"</span><span style="color: #0000ff">&gt;</span>$(PROGRAMFILES) (x86)<span style="color: #0000ff">&lt;/</span><span style="color: #800000">ProgramFiles32</span><span style="color: #0000ff">&gt;</span>
  <span style="color: #0000ff">&lt;</span><span style="color: #800000">ProgramFiles32</span> 
    <span style="color: #ff0000">Condition</span><span style="color: #0000ff">="$(ProgramFiles32) == ''"</span><span style="color: #0000ff">&gt;</span>$(PROGRAMFILES)<span style="color: #0000ff">&lt;/</span><span style="color: #800000">ProgramFiles32</span><span style="color: #0000ff">&gt;</span>
<span style="color: #0000ff">&lt;/</span><span style="color: #800000">PropertyGroup</span><span style="color: #0000ff">&gt;</span>

<span style="color: #0000ff">&lt;</span><span style="color: #800000">Exec</span> <span style="color: #ff0000">WorkingDirectory</span><span style="color: #0000ff">="src\app1"</span> 
  <span style="color: #ff0000">Command</span><span style="color: #0000ff">='"$(ProgramFiles32)\doxygen\bin\doxygen" Doxyfile'</span> <span style="color: #0000ff">/&gt;</span>
</pre>
</div>
<p>All he did is create a variable called ProgramFiles32 which would contain one of two file paths depending on whether the (x86) program files exists. He then uses that variable in his file path. It works reasonably well, and since I am not concerned with running this in any language other than English I am not too concerned with any problems which might arise from this. If this bites me down the road please point me back to this blog post.</p>
