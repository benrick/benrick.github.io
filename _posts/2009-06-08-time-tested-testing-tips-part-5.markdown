---
layout: post
title: "Time-Tested Testing Tips - Part 5"
date: 2009-06-08 12:22:00 -0400
comments: true
published: true
categories: ["blog", "Archive"]
tags: ["Blog"]
permalink: "/post/Time-Tested-Testing-Tips-Part-5/"
---
<!-- more -->



<p>Welcome back for another exciting tip for those developers writing unit tests. Today we will be looking at assertions in unit tests.</p>
<h3>Only Assert On One Case Per Test</h3>
<p>When people start writing unit tests they do the natural thing with their <em>Assert</em> statements; they write a bunch of them in the test. This makes a bunch of sense, because you don't want to repeat yourself in your tests. This is not bad <em>as long as all of the asserts are asserting the same expectation with different values</em>. If you are testing different <em>cases</em> then they need to be separate test.</p>
<p>The reason for this is that unit testing frameworks tend to abandon a test as soon as an assertion has failed, so you get less information if you have grouped many tests cases into one test method. By making sure that every test method contains only assertions dealing with the case in question, we will garner valuable information from each test. Maybe we will discover that the cases with negative numbers and the edge case, zero were the ones to fail. If we had grouped the assertions into one method, we would have only had one failed assertion and wouldn't have gotten all of this info. For example we might have only had zero fail if its assert was first, and then we would be thinking this was a problem with the edge case when it was really a problem with all numbers less than one.</p>
<h3>Group Your Asserts Together</h3>
<p>If you can, try to keep your asserts together at the end of the method. This will make them much easier to read and keep track of. I've seen some tests where someone wanted to assert before changing a value. A better way to handle this is to store the value you need to hang on to in a variable and assert at the end with everything else. This will make your tests a lot more maintainable, and someone down the road editing the test will sure thank you.</p>
<h3>Keep Your Assertions Concise</h3>
<p>You should have no logic in your assertions. Don't ever access a property or call a method in an assert statement. These are what someone looks at to try and figure out what is going on. Use simple, concise variable names which explain things. If assertions are cluttered and confusing, your tests will be very difficult to use.</p>
<p>Remember to be careful with your asserts. They should be clean, easy to read, and managed nicely. Their maintenance is extremely important to your tests.</p>
