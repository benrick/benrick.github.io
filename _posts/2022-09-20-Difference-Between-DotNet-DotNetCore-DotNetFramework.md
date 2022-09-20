---
layout: post
title: "What's the Difference Between .NET, .NET Core, and .NET Framework"
date: 2022-09-20 13:00:00 -0400
comments: true
published: true
categories: ["Archive"]
tags: [".NET", "dotnet", ".NET Core", ".NET Framework", "C#"]
permalink: "/post/Difference-Between-DotNet-DotNetCore-DotNetFramework/"
---

Even years after the changes, many people are confused by all of the different "dot nets" that have existed and still exist. Read on to find out what's going on and we'll remove that confusion around .NET Framework, .NET Core, .NET.

<p class="message">If you'd rather watch a video on this topic, you can check out my [What's the Difference between .NET Framework and .NET Core?](https://youtu.be/dLRd_LjVjNs) video on YouTube (or watch here).</p>

<div class="video-container">
    <iframe width="560" height="315" src="https://www.youtube.com/embed/dLRd_LjVjNs" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

## Abbreviated History of .NET

Let's understand the confusion by looking quickly at the history of our .NETs.

### Brief Early .NET History

The first of these ".NETs" we got was the .NET Framework, which was a framework for building Windows applications. It’s been around for decades and still runs many applications to this day.

![Early .NET Framework Logo](/images/files/2022-posts/CoreFrameworkConfusion/NET-Framework-Logo-2002.png){: width="50%"}

We had some variations of this that we won’t cover for now, but Microsoft eventually created an alternate option called .NET Core. Core removed the dependence on Windows, which allowed it to be cross-platform. It was neither a subset nor a superset of the existing .NET Framework, since they did take the chance to change some things as they removed some of the old baggage.

![.NET Core Logo](/images/files/2022-posts/CoreFrameworkConfusion/NET_Core_Logo.svg.png){: width="25%"}

### The Time of Parallel .NETs

After .NET Core came around, most of the people with connections to the developer division at Microsoft likely told you that .NET Core was the future, despite the many reassuring statements from Microsoft about fully supporting and maintaining the .NET Framework for years.

All of my new projects (that could be) were created on .NET Core, and I insisted to all of my clients that they follow the same policy. I'm glad we did, because .NET was/is the future of .NET (more on that below).

At this point, we had 2 separate .NET implementations, one that had a lot of legacy and was windows-focused and another without that legacy and was cross-platform. This alone had some confusion, since people didn’t know which to use for new projects. Some people thought that Framework was if you were on Windows only and Core was for non-Windows or both. That was wrong, but understandable how that mistake was made.

Many companies were not switching to .NET Core, because they thought it was an "alternate path", not the future of .NET.

### The Union of the .NETs

I wasn't in the backroom at Microsoft when they decided this, but I'm sure they were trying to figure out how to get everyone to switch to .NET Core and leave .NET Framework as a relic. Many companies were reluctant to put in the effort, so they decided to “merge” the two together into ".NET".

![.NET Logo](/images/files/2022-posts/CoreFrameworkConfusion/Microsoft_.NET_logo.svg.png){: width="25%"}

Since .NET Core's and .NET Framework's major version numbers were on 3 and 4 respectively, they decided to start the "merged" .NET at 5 (an increased number regardless of your starting point).

Awesome! So you might be wondering, what is this new .NET that isn’t Core or Framework, well, it is .NET Core, but they dropped “Core” from the name to make it clear that it’s the future and not an alternative. In doing this, they've removed the "is this the new path or an alternate path?" question.

## The Takeaway

At this point, we're in the same place we have been for a while. Your answer for, "which should I choose" is .NET latest version, not "Core" or "Framework" anymore.

![.NET Logo](/images/files/2022-posts/CoreFrameworkConfusion/Microsoft_.NET_logo.svg.png){: width="25%"}

If you **require** Core or Framework for some reason (highly unlikely that you do), you can create those, but the future is the .NET for any project you may start.

If you're building a Windows application, you can build WinForms, WPF, UWP, MAUI, etc. using .NET, so there's very little reason to pick Framework for those.

## Intentionally Not Covered Topics

You may have noticed that I didn't talk about any of the other .NETs that exist. I may explain those in future posts and/or videos, but I wanted to clear up this confusion without adding those extra bits that might make it harder to come across.

Have a great day, and happy coding, everyone!
