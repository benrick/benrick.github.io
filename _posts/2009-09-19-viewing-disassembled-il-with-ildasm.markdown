---
layout: post
title: "Viewing Disassembled IL with ILDASM"
date: 2009-09-19 15:04:00 -0400
comments: true
published: true
categories: ["blog", "Archive"]
tags: ["Blog"]
permalink: "/post/Viewing-Disassembled-IL-with-ILDASM/"
---
<!-- more -->



<p>For those of you who are simply computer geeks I present to you an easy way to view the generated intermediate language code that is generated when you&rsquo;re using the .NET Framework. So if you&rsquo;ve ever wanted to see what is generated from your compiler, so you can see what code gets executed at run-time you just need to take a few simple steps.</p>
<p>Open up the Visual Studio Command Prompt. You can find this command prompt in the Start Menu inside of the tools folder for Visual Studio.</p>
<p><img style="border-bottom: 0px; border-left: 0px; display: inline; border-top: 0px; border-right: 0px" title="VS-Command-Prompt" src="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/ViewingDisassembledILwithILDASM_D350/VS-Command-Prompt_3.jpg" border="0" alt="VS-Command-Prompt" width="500" height="251" /></p>
<p>From here you will be able to open up ILDASM&rsquo;s graphical user interface. Open it by typing &ldquo;ILDASM&rdquo;. It&rsquo;s a very simple program.</p>
<p><img style="border-bottom: 0px; border-left: 0px; display: inline; border-top: 0px; border-right: 0px" title="ILDASM-Start" src="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/ViewingDisassembledILwithILDASM_D350/ILDASM-Start_3.jpg" border="0" alt="ILDASM-Start" width="400" height="594" /></p>
<p>From here you will want to open up the assembled file you want to view. This could be a class library or an executable. In this example I will use a &ldquo;Hello World&rdquo; console application.</p>
<p><img style="border-bottom: 0px; border-left: 0px; display: inline; border-top: 0px; border-right: 0px" title="ILDASM-Project-Open" src="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/ViewingDisassembledILwithILDASM_D350/ILDASM-Project-Open_3.jpg" border="0" alt="ILDASM-Project-Open" width="318" height="384" /></p>
<p>The console application really only has one class. ILDASM_World.Program, which can be seen in the image. You can see the ILDASM_World namespace is where the class is located. Inside of the class we have a constructor (this is the default one I did not write the code for it). See this is neat, because we can see that a default constructor was created for us and we can see exactly what it does.</p>
<p>The Main method listed there is a standard one with a Console.Writeline(&ldquo;Hello World!&rdquo;); line written in it.</p>
<p>When we open up the method to view it we see the following IL is generated when we compile.</p>
<p><img style="border-bottom: 0px; border-left: 0px; display: inline; border-top: 0px; border-right: 0px" title="ILDASM-Main" src="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/ViewingDisassembledILwithILDASM_D350/ILDASM-Main_3.jpg" border="0" alt="ILDASM-Main" width="500" height="338" /></p>
<p>Now what is really cool here is that I bet pretty much every person reading this can figure out exactly what that code is doing. I think that people could have figured it out without my having to explain it. It is really cool to see. There are a lot of awesome tricks you can see here. Also if you&rsquo;re ever wondering what is going to happen when you compile something I recommend looking here. You&rsquo;ll be able to see exactly what actually happens.</p>
<p>This will assist you when you&rsquo;re writing your code since you&rsquo;ll be able to make a more educated decision on which approach to take with your code if you see what will be generated behind the scenes.</p>
<p>Your homework is to try this with loops and with a goto.</p>
