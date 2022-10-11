---
layout: post
title: "Treat Your Tests Well"
date: 2009-02-26 09:11:00 -0500
comments: true
published: true
categories: ["Archive"]
tags: ["TDD", "Unit Testing"]
permalink: "/post/Treat-Your-Tests-Well/"
---

<p>There are a lot of people starting to test, and some of them seem to have this misconception that test code is less important because it is, "just test code". I don't know how they come up with this crazy idea, but it creates some pretty ugly tests. When following the principles of Test Driven Development, it is important to realize that you will come back to these tests. You will look at them when they fail, you will adjust them when logic changes, and others will read them especially when they are trying to learn the system.</p>
<h4>Maintenance</h4>
<p>At some point you could perform maintenance on any piece of code in your application. THIS INCLUDES YOUR TESTS. When you need to go in and change them it better be easy. There better be code reuse, variable names better be descriptive, and you really need to have things organized well enough for you to find what you're looking for.</p>
<h4>Single Responsibility Principle</h4>
<p>The Single Responsibility Principle is a commonly followed principle when writing code, but I've seen people disregard it when writing tests. Your tests are extremely important. Don't make huge catchall test classes. Keep your test classes small and manageable. Each one should contain only a related group of tests. You will come back to these if you're testing correctly, and when you make changes you will write new tests or adjust old ones. Don't think for one second that you will never see your test classes after you write them. When you add new features and adjust old ones, you will need to open these files again.</p>
<p><strong>Test code is a first class citizen in your project. It is every bit as important as the rest of the project. Treat it as such or it will bite you back.</strong></p>
<h3>One Way Tests Differ From Other Code</h3>
<p>With tests, the specific details are a little bit more important than in other code. You still need code reuse for obvious reasons, so what do I mean here? All I am saying is that you don't want to hide things away in mysterious methods. Normally we extract methods to hide the details of some operation we are performing. We should be doing the same thing with test code, but we need to make one exception. When the details of that method are what you're testing, you <em>must</em> have them <em>in your test</em>.</p>
<p>In some instances you have an object with involves some complicated or at least tedious initialization, so you would want to hide that away in a method. For testing, however, it is important that you define the details of that initialization in the test method if they are important to the test.</p>
<p>As an example, we can say that we are working on a game, and we keep a <em>Points</em> property on our <em>Player</em> object. Maybe we want to make sure that after some action that would lose a player points, he doesn't go below a negative number. So we have a method that creates a player object for us. The problem is that we don't know what his initial points are set to if we don't either make that a parameter in the initialization method or set it after initialization. In some way we need to make sure that we define this <em>in our test method</em>.</p>
<p><em>Never ever let details you depend on be hidden away in some method where you can't see them in your test.</em></p>
<p>I've seen plenty of people use helper methods to initialize variables and such for their tests. This is a very bad idea if any of that information is important to that specific test. Only hide away unimportant details. For instance you might hide away the initialization of your mocked objects, but you would keep the player's points you will be Asserting the value of front and center. If values are being initialized in a non-test method you should be able to change those tests safely without causing problems.</p>
<p>Treat your tests well and they will be there to help you.</p>
