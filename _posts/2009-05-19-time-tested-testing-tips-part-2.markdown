---
layout: post
title: "Time-Tested Testing Tips - Part 2"
date: 2009-05-19 22:25:00 -0400
comments: true
published: true
categories: ["blog", "Archive"]
tags: ["Blog"]
permalink: "/post/Time-Tested-Testing-Tips-Part-2/"
---
<!-- more -->



<p>In the <a href="/post/2009/05/19/Time-Tested-Testing-Tips-Part-1.aspx">first part of this series of testing tips</a>, I mentioned a couple of tips I believe to be quite useful. I am going to continue this series today by writing about a couple of more ways to write better tests. I also plan to give reasons for testing and describe different benefits of the practice as I go.</p>
<h3>Test Driven Development</h3>
<p>Yes, I am going to bring this up. Plenty of people have latched onto the idea that testing code helps make code better. A lot of people even believe that it makes the process of writing the code faster. I see a lot of people who are reluctant still to use test driven development. I know I am throwing around a buzzword&hellip; or maybe I mean buzzphrase since that&rsquo;s actually three words.</p>
<p>I don&rsquo;t plan on doing TDD justice here since I am trying to keep these tips relatively short. I just hope this is enough to inspire people to go read, learn more, and try some test driven development. I am going to give some quick reasons why developers testing their code should write the tests first.</p>
<ul>
<li><strong>You will not want to go back and write it later.</strong> Sometimes you are going to go back and write the tests for the code you have already written, but what happens if you decide you&rsquo;re going to write a lot of code and then go back and add the tests. Now you&rsquo;re talking about a lot of testing all at once. There is a good chance you&rsquo;ll cut corners and maybe skip entire aspects of the testing. I know I would be tempted.</li>
<li><strong>How do you know what kind of interface your new code needs if you&rsquo;ve never used it?</strong> If you start by trying to use some code that does not exist yet, you&rsquo;ll be deciding how you would want to use it. Now you&rsquo;re probably thinking you could do that anyway. If you write code to use some new feature you will know the design is easy to use and work with. You just made it up and used it in the test. If you didn&rsquo;t write the test you had to guess what interface you will want later.</li>
</ul>
<h3>Organize, Refactor, and Take Care of Your Tests</h3>
<p>I recommend you repeat this daily, &ldquo;My test code is just as important as my production code&rdquo;. I think this is a very good point to remember when you&rsquo;re writing tests. All of those principles you apply when writing production code should be followed with test code. DRY, SOLID, YAGNI, etc. are all important even with the testing code.</p>
<p>Obviously duplicating code can make your tests difficult to maintain. What if some business logic changes? If you were repeating yourself you now have the fun task of going through a dozen tests changing each one, but if you had not repeated the same code you might have been able to update one location in the test code. A lot of people are concerned when the line count of a single file gets large and they will refactor it into multiple manageable files. This same policy should apply to test classes. If you&rsquo;ve ever gone into a test class with way too many classes, you probably know how difficult it can be to maintain.</p>
<p>Tests exist to make development easier, and if they become difficult to maintain then something needs to change. I certainly don&rsquo;t advocate spending large amounts of time refactoring the tests, but since they are supposed to increase the longevity of the application they must also be maintained.</p>
<h3>Adjust Your Style to Your Test Framework</h3>
<p>I obviously recommend that everyone use a testing framework. There are plenty of them out there, and they supply a great deal of the tools you&rsquo;ll need for testing. They come in all languages, flavors, and colors. You might look into these <a href="http://www.nunit.org/">NUnit</a>, <a href="http://msdn.microsoft.com/en-us/library/ms182409(VS.80).aspx">MSTest</a>, <a href="http://www.junit.org/">JUnit</a>, <a href="http://apps.sourceforge.net/mediawiki/cppunit/index.php?title=Main_Page">CppUnit</a>. What is important is that you make sure you know how your tools work so you can test best with them.</p>
<p>I will elaborate on a couple of examples and perhaps down the road I&rsquo;ll give some more specific examples.</p>
<p>Some tools show you a list of test names, and only minor details about why the test failed. For this you usually need to go the a description view or something similar. In these cases it is important to name your tests effectively.</p>
<p>As an example if I have a method called <em>Add</em> and it takes two parameters <em>a</em> and <em>b</em>. I might write a test for that method. If I name my test <em>TestAdd</em>, and that test fails you know something is wrong in that method, but you do not know what failed. If I had instead made a few more specific methods you could glean more information from the test having failed. Some examples of tests I might create are <em>AddTwoZerosShouldBeZero</em>, <em>AddNumberToZeroShouldBeTheNumber</em>, <em>AddPositiveNumbersTest</em>, <em>AddNegativeNumbersTest</em>, etc.</p>
<p>Some parts I would lump together like positive numbers and negative numbers. It is important to handle a couple of different scenarios as well as the <em>edge cases</em>. I could have done negative and natural numbers and that would cover all numbers, but I wanted to make sure the edge case, zero, was handled correctly, so I test it separately.</p>
<p>People can argue back and forth all day long about whether you should have a lot of small tests or group them together, but this is what has worked well for me in the past and I hope it works well for you also.</p>
