---
layout: post
title: "3 Things You Didn't Know VS Code Can Do - Part 4, Custom File Icons, Keyboard Shortcuts, and Import Keymaps"
date: 2022-10-07 01:00:00 -0400
comments: true
published: true
categories: ["VS Code Tips and Tricks", "Archive"]
tags: ["VSCode", "Tips and Tricks", "YouTube Video"]
permalink: "/post/3-Things-You-Did-Not-Know-VSCode-Can-Do-Part4/"
---

Did you know that you can customize the file icons in VS Code explorer, customize and search the keyboard shortcuts in VS Code, view a printable keyboard shortcut cheat sheet, and import the keymaps from other editors into VS Code?

<div class="message">
I've been creating a series of videos on YouTube about cool things in VS Code that you may not know about. Check out the [DevChatter YouTube Channel](https://www.youtube.com/c/devchatter) if you want to see all of my videos, or you can see the [VS Code Tips](https://youtube.com/playlist?list=PLfRLz7YT8uz36VdgSMATJj2chNtbixokI) Playlist.
</div>

<div class="video-container">
    <iframe width="560" height="315" src="https://www.youtube.com/embed/204EW3cX1zM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

## Changing the File Icons in VS Code

You can change the theme of the file icons in VS Code Explorer Sidebar by opening up the File Icon Theme menu. You can open it from the manage menu (the gear in the sidebar) by selecting `File Icon Theme` or by opening the commands menu `[F1]` or `[Ctrl]` + `[Shift]` + `[P]` and searching for "File Icon Theme".

### Opening File Icon Menu from Manage Menu

![Opening File Icon Menu from Manage Menu](/images/files/2022-posts/VSCodeTips/Part4/FileIconMenuFromManageMenu.png)

### Opening File Icon Menu from Command Menu

![Opening File Icon Menu from Command Menu](/images/files/2022-posts/VSCodeTips/Part4/FileIconMenuFromCommandMenu.png)

Once open, you can preview the file icon themes by using the up and down arrows to select each of the installed icon themes. You can click on the theme you like to change to it. If you select the last item, `Install Additional File Icon Themes...`, it will open the `Extensions` sidebar showing results for extensions to change the file icon theme.

![File Icon Extension Search Results in VS Code](/images/files/2022-posts/VSCodeTips/Part4/FileIconExtensionsSearch.png)

You can open and see details of each extension to choose which (if any) you want to install. Just install them by clicking the `Install` button (like a normal extension). Once installed, you can open up the `File Icon Menu` again to preview or change your newly installed file icon themes.

## Keyboard Shortcuts in VS Code

There are more keyboard shortcuts in VS Code than most of us can remember. Luckily, we don't have to remember them all, since VS Code has a `Keyboard Shortcuts` window that allows searching for shortcuts.

You can open the `Keyboard Shortcuts` window from the manage menu (the gear in the sidebar), from `File` -> `Preferences` -> `Keyboard Shortcuts`, by opening the commands menu `[F1]` or `[Ctrl]` + `[Shift]` + `[P]` and searching for "Open Keyboard Shortcuts", or by using the keyboard shortcut `[Ctrl]` + `[K]` + `[S]`.

### Opening Keyboard Shortcuts from Manage Menu

![Opening Keyboard Shortcuts from Manage Menu](/images/files/2022-posts/VSCodeTips/Part4/KeyboardShortcutsMenuFromManageMenu.png)

### Opening Keyboard Shortcuts from Command Menu

![Opening Keyboard Shortcuts from Command Menu](/images/files/2022-posts/VSCodeTips/Part4/OpenKeyboardShortcutsFromCommandMenu.png)

### Opening Keyboard Shortcuts from File Menu

![Opening Keyboard Shortcuts from File Menu](/images/files/2022-posts/VSCodeTips/Part4/KeyboardShortcutsMenuFromFileMenu.png)

Once you've opened the keyboard shortcuts window, you can use the search box to search for any possible actions that can have a keyboard shortcut set for it. With any of the items in the list, you can also change any of the shortcuts if you want to.

![Search VS Code Keyboard Shortcuts](/images/files/2022-posts/VSCodeTips/Part4/KeyboardShortcutsMenuSearchResults.png)

If you want a printable set of the default keyboard shortcuts, you can find a link to it inside of VS Code (for your operating system) by opening the commands menu `[F1]` or `[Ctrl]` + `[Shift]` + `[P]` and searching for "Keyboard Shortcuts Reference" or by using the keyboard shortcut `[Ctrl]` + `[K]` + `[R]` (remember it as **K**eyboard **R**eference).

- [VS Code Windows Keyboard Shortcut Reference](https://code.visualstudio.com/shortcuts/keyboard-shortcuts-windows.pdf)
- [VS Code Linux Keyboard Shortcut Reference](https://code.visualstudio.com/shortcuts/keyboard-shortcuts-linux.pdf)
- [VS Code Mac Keyboard Shortcut Reference](https://code.visualstudio.com/shortcuts/keyboard-shortcuts-macos.pdf)

## Importing Other IDE Keymaps into VS Code

VS Code isn't the first editor I've ever used. In fact, I've used and know the keyboard shortcuts to Visual Studio, Rider, WebStorm, Notepad++, etc. When I'm switching between them, it's definitely a challenge to switch my brain to thinking of the correct set of shortcuts. If I wanted to make it easier, I could import the full keymap of another IDE into VS Code.

To migrate your keyboard shortcuts from another editor, open the manage menu (the gear in the sidebar) and choose `Migrate Keyboard Shortcuts from...`, which will open up the `Extensions` sidebar showing the results of a search for keymaps.

![Open VS Code Keymaps Import](/images/files/2022-posts/VSCodeTips/Part4/MigrateKeyboardShortcutsFromManageMenu.png)

![VS Code Keymaps Extensions Install](/images/files/2022-posts/VSCodeTips/Part4/KeymapExtensionsResults.png)

Many of these will do more than just a keymap import, so read the extension details for how to use the one for your editor.

Have fun!
