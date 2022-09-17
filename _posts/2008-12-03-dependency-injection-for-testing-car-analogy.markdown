---
layout: post
title: "Dependency Injection for Testing - Car Analogy"
date: 2008-12-03 10:37:00 -0500
comments: true
published: true
categories: ["blog", "Archive"]
tags: ["Blog"]
permalink: "/post/Dependency-Injection-for-Testing-Car-Analogy/"
---
<!-- more -->



<p>One analogy I like using when talking about interfaces is the car. I like it because cars have a standard "interface" and most people know how to drive cars. In a post I wrote recently about <a href="/post/simple-dependency-injection/" target="_blank">dependency injection</a>, I mentioned the importance of programming against interfaces instead of concrete classes.</p>
<p>For my car analogy I will start by saying that you are the program. You have been programmed against an interface. This is a good thing. You know how to drive a car. In this case "Car" is the interface. (Remember this means a literal interface, so it could be an abstract class.) You learned to drive a car. It doesn't matter what brand make or model. Since you know how to drive a car you can drive anything that implements the car interface even if it is not a car.</p>
<p>When you need to get from one place to another you can use any car with the same interface you know. This is very useful. You may not know how to operate all the features (methods) of that specific car. For example do you might not know how to operate the extra parts of a tow truck, but you could still drive it.</p>
<p>I like that analogy for interfaces.</p>
<h3>How does testing fit this analogy?</h3>
<p>Notice that I said earlier that, "you can drive anything that implements the car interface even if it is not a car". So before you can get your license to drive in the United States you need to pass a test. That is kind of like testing. Well there are two ways we could test your driving.</p>
<p>Right now the current system used to test drivers is an integration test. Perhaps in the future we will have a nice unit test to test our drivers. I am obviously going somewhere with this, so I will get straight to the point.</p>
<p>The way we test drivers now is we have someone sit in the car and watch what you do. We have to have very predictable courses set up in advance. We also have trouble controlling external variables (other drivers on the road). We can't control the weather for these tests, but they will be there when you're taking the test. Observations are made by an external entity (the person testing you) one that can't always get the exact interactions being made. All of these external resources even when they're controllable make this an integration test. We are dependent on too many other things.</p>
<p>A unit test for testing how well someone drives would need to break the dependency on a car by using an interface. We've done that. We are saying that a person knows the "car interface". Now we need some fake car that we can use for testing purposes to remove that piece we don't control. One that records all the interactions that the driver makes with the car, so we're not dependent on external observations of what is going on. We also need to break the dependency on real roads, since traffic conditions and the environment are difficult to change, control, and standardize. What does that sound like to me? A video game or in more professional terms; a simulator. The driver can sit down with this thing which has the same interface as a car, behaves as a car, works like a car. We can give the driver any scene, environment, conditions, etc. we want. We can also accurately measure all interactions with our fake car.</p>
<p>Maybe some day we will actually test drivers this way. It certainly would make it faster and easier to test. We could test more often. Considering that once someone has a license we don't test them again....</p>
<p>Would you do that with your code? I run unit tests every time I make a small change. Integration tests every time I check in.</p>
