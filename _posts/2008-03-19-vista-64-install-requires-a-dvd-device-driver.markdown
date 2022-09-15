---
layout: post
title: "Vista 64 Install Requires a DVD Device Driver"
date: 2008-03-19 21:31:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Orcs Goblins  and .NET"]
permalink: "/post/Vista-64-Install-Requires-a-DVD-Device-Driver/"
---
<!-- more -->

<p>So I've been using Vista 32 for a while now. I've not had much trouble with it. I've not seen the horrors about which others speak. Perhaps now my eyes have opened a little bit to some of the problems. So while installing Windows Vista 64 on a machine, the installer said it needed a driver for the CD/DVD device. So at this point I am a bit confused. It makes no sense. If it could boot from the disc why can't it install from the disc. It can read the disc perfectly well. How else could it have booted from the disc?</p>
<p>After scouring a few forums trying to find the answer, I found a few interesting suggestions. While on 3rd party sites, I got suggestions of buying new devices or installing drivers in windows. Some suggestions of getting the drivers loaded during installation. On Microsoft forums I saw a lot of comments saying, "tell company x to write drivers for 64 bit". OK, thanks guys. It is an optical disc drive, and any OS installer should be able to boot pretty much any optical drive with minimal compatibility and install.</p>
<p>I eventually found one suggestion which seemed a bit crazy, "Change the IDE settings". So I figured I would try rewiring the device and see what happened. As it turned out for me if the drive was not set as the secondary slave, Vista 64 would not install. Just try and tell me that doesn't seem crazy.</p>
<p><strong>The Solution that worked for me: Change the IDE settings so that the DVD Drive is the Secondary Slave.</strong></p>
<p>Enjoy Windows Vista 64.</p>
