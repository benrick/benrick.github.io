---
layout: post
title: "Silverlight 3 Out of the Browser"
date: 2009-09-15 16:43:00 -0400
comments: true
published: true
categories: ["Archive"]
tags: ["Blog"]
permalink: "/post/Silverlight-3-Out-of-the-Browser/"
---
<!-- more -->



<p>Running a Silverlight application out of the browser is very powerful. This lets users install a Silverlight application locally with a quick right click on the app in the browser. In earlier versions of Silverlight this was still pretty easy, but now you don&rsquo;t even have to open up an xml file to do it.</p>
<p>So here is my simple Silverlight application running in the browser.</p>
<p><img style="border-bottom: 0px; border-left: 0px; display: inline; border-top: 0px; border-right: 0px" title="InitialMessageInBrowser" src="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/Silverlight3OutoftheBrowser_E7F1/InitialMessageInBrowser_3.png" border="0" alt="InitialMessageInBrowser" width="509" height="349" /></p>
<p>After I click that Button the app makes a web service call to change the text, which isn&rsquo;t that important to this demo. I figured it was better than having it do nothing.</p>
<p><img style="border-bottom: 0px; border-left: 0px; display: inline; border-top: 0px; border-right: 0px" title="AfterClickInBrowser" src="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/Silverlight3OutoftheBrowser_E7F1/AfterClickInBrowser_3.png" border="0" alt="AfterClickInBrowser" width="509" height="349" /></p>
<p>Hooray we have a working Silverlight application. Now in order to get it running out of the browser we have only a couple of steps to take. None of which involve going into the AppManifest.xml file like was required in previous versions. Now we simply right-click on the Silverlight project in Visual Studio and select <em>Properties</em>.</p>
<p><img style="border-bottom: 0px; border-left: 0px; display: inline; border-top: 0px; border-right: 0px" title="SilverlightProperties" src="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/Silverlight3OutoftheBrowser_E7F1/SilverlightProperties_3.png" border="0" alt="SilverlightProperties" width="500" height="259" /></p>
<p>After enabling the ability to run out of the browser you just need to change the Out-of-Browser Settings. Doing this will create a file in the properties folder of the Silverlight application which has XML defining all of the settings configured here. This GUI just makes it easy to set up.</p>
<p><img style="border-bottom: 0px; border-left: 0px; display: inline; border-top: 0px; border-right: 0px" title="OutOfBrowserSettings" src="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/Silverlight3OutoftheBrowser_E7F1/OutOfBrowserSettings_3.png" border="0" alt="OutOfBrowserSettings" width="520" height="523" /></p>
<p>I like how simple this is. Not overloaded with tons of options. Just easy to use.</p>
<p>Now when we run the app we can right-click on the application and we are able to install the app locally.</p>
<p><img style="border-bottom: 0px; border-left: 0px; display: inline; border-top: 0px; border-right: 0px" title="RightClickInstall" src="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/Silverlight3OutoftheBrowser_E7F1/RightClickInstall_3.png" border="0" alt="RightClickInstall" width="507" height="349" /></p>
<p>When we click on the Install option we get a nice installation wizard with no complexity.</p>
<p><img style="border-bottom: 0px; border-left: 0px; display: inline; border-top: 0px; border-right: 0px" title="InstallApp" src="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/Silverlight3OutoftheBrowser_E7F1/InstallApp_3.png" border="0" alt="InstallApp" width="466" height="201" /></p>
<p>All the user has to do is decide where to put a shortcut. Once they click this the app will be installed and running. The application will look a little bit like this.</p>
<p><img style="border-bottom: 0px; border-left: 0px; display: inline; border-top: 0px; border-right: 0px" title="InitialMessageOutOfBrowser" src="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/Silverlight3OutoftheBrowser_E7F1/InitialMessageOutOfBrowser_3.png" border="0" alt="InitialMessageOutOfBrowser" width="423" height="352" /></p>
<p>And when we click out button we get another web service call and this time we pass a different parameter to the service call and get a different message. Take a look.</p>
<p><img style="border-bottom: 0px; border-left: 0px; display: inline; border-top: 0px; border-right: 0px" title="AfterClickOutOfBrowser" src="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/Silverlight3OutoftheBrowser_E7F1/AfterClickOutOfBrowser_3.png" border="0" alt="AfterClickOutOfBrowser" width="423" height="352" /></p>
<p>So how easy was that? Say that the user wants to uninstall the application now. That is also easy. All they have to do is right-click on it and select the option to remove the app and it is gone. They can do this in or out of browser.</p>
<p><img style="border-bottom: 0px; border-left: 0px; display: inline; border-top: 0px; border-right: 0px" title="RemoveApp" src="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/Silverlight3OutoftheBrowser_E7F1/RemoveApp_3.png" border="0" alt="RemoveApp" width="423" height="352" /></p>
<p>So now you know how easy it is to set up an out of browser Silverlight application.</p>
