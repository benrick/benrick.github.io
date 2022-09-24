---
layout: post
title: "3 Things You Didn't Know VS Code Can Do - Set 1"
date: 2022-09-26 11:00:00 -0400
comments: true
published: true
categories: ["VS Code Tips and Tricks", "Archive"]
tags: ["VSCode", "Tips and Tricks"]
---

I've been creating a series of videos on YouTube about cool things in VS Code that you may not know about. Check out the [DevChatter YouTube Channel](https://www.youtube.com/c/devchatter) if you want to see all of my videos, or you can see the [VS Code Tips](https://youtube.com/playlist?list=PLfRLz7YT8uz36VdgSMATJj2chNtbixokI) Playlist.

<div class="video-container">
    <iframe width="560" height="315" src="https://www.youtube.com/embed/dwBgIxgXlFU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

## Paste JSON as Code in VS Code

While VS Code doesn't have a built-in way of posting, there is an extension that will do it. Grab the [Paste JSON as Code Visual Studio Code Extension](https://marketplace.visualstudio.com/items?itemName=quicktype.quicktype).

![Paste JSON as Code in VS Code Extension](/images/files/2022-posts/VSCodeTips/PasteJsonExtension.png)

Copy your JSON onto your clipboard, open the file where you want to paste the types.

![]()

Press F1 or Ctrl Shift P to open the commands menu, and search for "paste" to find the commands for `Paste JSON as...`.

![](/images/files/2022-posts/VSCodeTips/VSCodePaseCommand.png)

If it can't infer the language from the file extension you're pasting into, it will ask you to choose a language. If it did know, it will skip this question.

![]()

JSON always has a root object (the outer curly braces), but that object doesn't have a name, so the extension will now ask you to name that root object.

![]()

After clicking enter, there will be one or more types created in your file, depending on the complexity of the JSON you were using. It will try to detect types and includes metadate. You can change this data as you like. The command was just to help get you started.

![]()

## Search for Files By Word in VS Code

When you're looking for a file using the search in VS Code, you can search based on the first letters of the words in the name of the file.

To see this in action, open up the file search using Ctrl P. Then type in upper case letters, only the first letter of each word, so if you wanted to find `SpecialBikeFactory.cs`, you might type "SBF" into the search box.

![]()

In addition, you can continue searching more of the word after each of those capitals, so "SpBiFa" would be a great search term if your codebase is large and has more than one type for "SBF".

![]()

## Make Whitespace Visible in VS Code

In some languages, like Python, whitespace matters. In languages where whitespace matters less, it's still important for formatting. In Visual Studio Code, you can make the whitespace visible. To do this, go to the `View` menu and select `Render Whitespace`. Doing this will show spaces as dots and tabs as arrows.

![]()
