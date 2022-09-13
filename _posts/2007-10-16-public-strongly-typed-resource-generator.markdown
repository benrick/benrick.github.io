---
layout: post
title: "Public Strongly Typed Resource Generator"
date: 2007-10-16 17:30:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Orcs Goblins  and .NET"]
alias: ["/post/Public-Strongly-Typed-Resource-Generator", "/post/public-strongly-typed-resource-generator"]
---
<!-- more -->

<p>I recently installed an interesting custom tool. It is an <a href="http://www.codeproject.com/dotnet/ResXFileCodeGeneratorEx.asp" target="_blank">Extended version of the resource generator in Visual Studio</a>. The nicest part of this for me is that this one is public instead of internal like the default one. In order to have a centralized resource file it needs to be usable between projects in Visual Studio, but the internal class made this difficult. I could just manually update the generated code each time after using the file, but that would just be stupid.</p>
<p>This is a&nbsp;great&nbsp;answer to&nbsp;the problem I needed to solve&nbsp;because it allows me to keep the resource file in one spot and not have to do and weird tricks to accomplish my goals.</p>
<p>The article accompanying this tool is well-written and explains a bit about how to use and install it.</p>
<p>This little tool is easy to install. It comes with an MSI installer or the source code whichever you prefer. I'd say just go with the MSI.</p>
<p>Note: Make sure if you are on Vista you run it as administrator though or it will not work. Since it is an MSI file you will not see an option to run as administrator, so you will want to create a batch file to do this. In the batch file you will execute the MSI file. You will run the batch file as administrator. The following code should be in the batch file.</p>
<p>msiexec /i "Absolute path to the installer \ResXFileCodeGeneratorEx.msi"</p>
<p>That should get it installed. You then need to create a resource file and in the "Custom Tool" field of the properties window&nbsp;type "ResXFileCodeGeneratorEx" into the field. This will then make your new generated Strongly Typed resources a public class.</p>
<p>Congratulations you may now use your resource file between projects!</p>
