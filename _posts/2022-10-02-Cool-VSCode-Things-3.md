---
layout: post
title: "3 Things You Didn't Know VS Code Can Do - Part 3"
date: 2022-10-02 01:00:00 -0400
comments: true
published: true
categories: ["VS Code Tips and Tricks", "Archive"]
tags: ["VSCode", "Tips and Tricks", "YouTube Video"]
permalink: "/post/3-Things-You-Did-Not-Know-VSCode-Can-Do-Part3/"
---

Did you know that you can change your themes in VS Code, use a keyboard shortcut to open the VS Code settings, make changes by searching the settings window, and synchronize your settings across multiple instances of VS Code?

<div class="message">
I've been creating a series of videos on YouTube about cool things in VS Code that you may not know about. Check out the [DevChatter YouTube Channel](https://www.youtube.com/c/devchatter) if you want to see all of my videos, or you can see the [VS Code Tips](https://youtube.com/playlist?list=PLfRLz7YT8uz36VdgSMATJj2chNtbixokI) Playlist.
</div>

<div class="video-container">
    <iframe width="560" height="315" src="https://www.youtube.com/embed/1eiMpsEWigI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

## Changing the Theme in VS Code

You can change the theme in VS Code by opening up the Color Theme menu. You can open it in one of 3 ways: opening it from the manage menu (the gear in the sidebar), opening it with the keyboard shortcut `[Ctrl]` + `[K]` + `[T]`, or opening the commands menu `[F1]` or `[Ctrl]` + `[Shift]` + `[P]` and searching for "Color Theme".

Opening Theme Menu from Manage Menu

![Opening Theme Menu from Manage Menu](/images/files/2022-posts/VSCodeTips/Part3/ManageMenuOpenTheme.png)

Opening Theme Menu from Command Menu

![Opening Theme Menu from Command Menu](/images/files/2022-posts/VSCodeTips/Part3/CommandMenuOpenTheme.png)

## Searching the Settings in VS Code

There are many settings buit into VS Code, and many others included as part of extensions. For this reason, it can be hard to keep track of and know all of the different settings, which is why VS Code allows you to search for settings. You can open the `Settings` window from the manage menu (the gear in the sidebar), from `File` -> `Preferences` -> `Settings`, or by using the keyboard shortcut `[Ctrl]` + `[,]`.

Opening Settings from Manage Menu

![Opening Settings from Manage Menu](/images/files/2022-posts/VSCodeTips/Part3/ManageMenuOpenSettings.png)

Opening Settings from Command Menu

![Opening Settings from Command Menu](/images/files/2022-posts/VSCodeTips/Part3/CommandMenuOpenSettings.png)

Opening Settings from File Menu

![Opening Settings from Command Menu](/images/files/2022-posts/VSCodeTips/Part3/FileMenuOpenSettings.png)

Once you've opened the settings screen, you can use the search box to search for a term and it will filter the results to those settings matching your search term. In addition, notice that the left navigation of settings also filters down to the settings matching your search.

![Search VS Code Settings](/images/files/2022-posts/VSCodeTips/Part3/SearchSettings.png)

## Syncing the Settings in VS Code

I'm writing this post on my laptop using VS Code. On a daily basis, I work on multiple laptop computers and desktop computers. Each of these machines has VS Code installed on it. If I make changes to the settings in one, it would be nice if that replicated to the others. In years past, many of us found ways of automating this process in our various editors using cloud file storage to transfer settings file changes (and similar solutions).

No longer must we implement our own syncing, since VS Code has a built-in settings syncronization system. As long as you have a GitHub or Microsoft account to log into, you can have VS Code sync your settings.

Open up your settings menu as we did above and click on the `Turn on Settings Sync` button in the uppper right side of the Settings window.

![Turn on Settings Sync in VS Code Button](/images/files/2022-posts/VSCodeTips/Part3/VSCodeSettingSyncButton.png)

Once open, you'll need to choose which settings you want to sync and then click the button to log into your account to sync the settings.

![Settings Sync Options in VS Code](/images/files/2022-posts/VSCodeTips/Part3/VSCodeSettingSyncOptions.png)

After clicking log in, you'll need to choose which type of account to log into.

![Settings Sync Options in VS Code](/images/files/2022-posts/VSCodeTips/Part3/VSCodeSettingSyncLoginOptions.png)

This should now open a browser that takes you to the appropriate authentication screen and allows you to login. After logging in through the browser, it should share that permission with VS Code and syncing should now be happening.

Have fun!
