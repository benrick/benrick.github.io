---
layout: post
title: "Unpacking Tuples in Python"
date: 2007-12-11 17:37:00 -0500
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Orcs Goblins  and .NET", "Orcs Goblins  and .NET"]
permalink: "/post/Unpacking-Tuples-in-Python"
---
<!-- more -->

<p>There are plenty of reasons why I like the Python language. Yes, I know it is an interpreted language and it is very dynamic. While looking at some JavaScript mere moments ago, I saw someone pass back two values from a function. This is one thing that bothers me when I am writing in a lot of languages. I will need to pass back two or more values from my function. So I need to change the return value to some type of a sequence perhaps an array. Then I need to adjust the location where I call the function so that it accepts and array. It then needs to take each value of the array and place the returned value into each variable that needs the value.... Yuck! What a pain just to get a couple of values!</p>
<p>A lot of times I just want a simple solution to my problem. I'd like to type 2 lines of code instead of 5. Python has plenty of problems, but one of my favorites assets of the Python language is the ability to Unpack tuples from functions. So lets say that I want to return three values from my function. I just separate them by commas and it works. I then in my function call just list each variable to which those values correspond separated by commas and away I go.</p>
<p>&nbsp;</p>
<pre>def GetBestHotel()
    # Logic Goes Here
    return name, location, cost

hotelName, hotelLocation, hotelCost = GetBestHotel()
</pre>
<p>&nbsp;</p>
<p>Isn't that a neat trick. I just listed each variable and Python unpacked that tuple (basically an array) and it put each of the values in the correct variables. No extra variable declarations and I didn't have to have an assignment statement for each of the values being returned. Now that is convenience. This is obviously a very specialized little feature, but I do enjoy having it available. It is always good to know of the useful tricks of any language you use.</p>
