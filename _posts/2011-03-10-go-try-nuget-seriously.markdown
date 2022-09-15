---
layout: post
title: "Go Try NuGet. Seriously."
date: 2011-03-10 09:32:00 -0500
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Blog"]
permalink: "/post/Go-Try-NuGet-Seriously/"
---
<!-- more -->



<p>NuGet is best described as the tool from Microsoft that lets you add references to your project directly from the NuGet feed while storing and managing them locally. It lets you keep your <a href="/post/Organizing-Software-Projects.aspx" target="_blank">references local to your source code</a>, which will help you keep your software project encapsulated. When a package you use gets an update, you can ask NuGet to update your local version of the package.</p>
<p>When telling people about <a href="http://nuget.org/">NuGet</a>&nbsp;it is important to explain how powerful it really is. NuGet is not just a collection of libraries to include in your bin folder. It will actually install the package into your project. I will show you what I mean.</p>
<h3>Installing NuGet</h3>
<p>NuGet can be installed through the Visual Studio Extension Manager. From within Visual Studio, open the <em>Tools</em> menu and select <em>Extension Manager</em>. Once in that window, select the Online Gallery and search for “nuget”. Then you just have to tell it to Download nuget. This will require a restart of Visual Studio.</p>
<p><a href="/images/files/NugetExtensioinManager.png"><img style="background-image: none; border-right-width: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="NugetExtensioinManager" src="/images/files/NugetExtensioinManager_thumb.png" border="0" alt="NugetExtensioinManager" width="550" height="380"></a></p>
<h3>Using NuGet to Install a Package</h3>
<p>Now that NuGet is installed we can start using it. There are two ways to do this, and I will start with the one that is the easiest. All we need to do is right click on out project’s references folder and select “Add Library Package Reference…”</p>
<p><a href="/images/files/NugetAddReferenceContextMenu.png"><img style="background-image: none; border-bottom: 0px; border-left: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top: 0px; border-right: 0px; padding-top: 0px" title="NugetAddReferenceContextMenu" src="/images/files/NugetAddReferenceContextMenu_thumb.png" border="0" alt="NugetAddReferenceContextMenu" width="308" height="289"></a></p>
<p>From the window that opens, we want to make sure that we select the <em>Online</em> section on the left and select <em>All</em>. Now we use the search box to search for the package that we’re trying to install. And we click the <em>Install</em> button. NuGet will get the package you requested as well as any Dependencies listed. Notice in the following image that WebActivator is listed as a dependency of this package. NuGet packages will often add files other than just dlls to your solution. <a href="http://isis.codeplex.com/" target="_blank">Isis</a>, which is the package shown here will also include its own bootstrapper, which will allow Isis to have routes mapped for itself, so you can begin using the application immediately.</p>
<p><a href="/images/files/NugetInstallIsis.png"><img style="background-image: none; border-bottom: 0px; border-left: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top: 0px; border-right: 0px; padding-top: 0px" title="NugetInstallIsis" src="/images/files/NugetInstallIsis_thumb.png" border="0" alt="NugetInstallIsis" width="550" height="367"></a></p>
<h3>Viewing the Results of Installing a Package From NuGet</h3>
<p>Thanks to packages being able to includes these files allowing themselves to be automatically configured, I already have the <a href="http://isis.codeplex.com/" target="_blank">Isis ASP.NET Control Panel</a> installed. It’s not just a reference in my bin folder, it also gave me this bootstrapper file. I don’t have to do any extra work installing Isis.</p>
<p><a href="/images/files/SolutionAfterIsisInstall.png"><img style="background-image: none; border-bottom: 0px; border-left: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top: 0px; border-right: 0px; padding-top: 0px" title="SolutionAfterIsisInstall" src="/images/files/SolutionAfterIsisInstall_thumb.png" border="0" alt="SolutionAfterIsisInstall" width="308" height="357"></a></p>
<p>Thanks to NuGet getting me all the files I can navigate to the Isis ASP.NET Control and begin using it immediately.</p>
<p><a href="/images/files/IsisControlPanel.png"><img style="background-image: none; border-bottom: 0px; border-left: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top: 0px; border-right: 0px; padding-top: 0px" title="IsisControlPanel" src="/images/files/IsisControlPanel_thumb.png" border="0" alt="IsisControlPanel" width="550" height="460"></a></p>
<p>There is also a command line interface for NuGet. If that is your cup of tea, then I recommend checking it out instead.</p>
<h3>The Isis ASP.NET Control Panel</h3>
<p>In case you are wondering about the <a href="http://nuget.org/List/Packages/isis" target="_blank">Isis package</a> that I installed, it is a relatively new Open Source project based on a few projects that Steve Smith and I have worked on in the past. We are creating an ASP.NET control panel which can be easily installed (as you’ve seen already) into any ASP.NET application and provide tools to help manage, develop, and diagnose the application.</p>
