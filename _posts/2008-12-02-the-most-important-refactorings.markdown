---
layout: post
title: "The Most Important Refactorings"
date: 2008-12-02 11:33:00 -0500
comments: true
published: true
categories: ["Archive"]
tags: ["Unit Testing"]
permalink: "/post/The-Most-Important-Refactorings/"
---

<p>Testing and refactoring go hand in hand. When tests are in place we are safer to refactor because we have test in place which will help us preserve the previous functionality. When we are trying to add tests into code, we refactor the code to make it more testable. We refactor so we can test and we test so we can refactor. This may seem a bit cyclic, but both the refactoring and the tests improve our code. This makes it quite important to do them both anyway.</p>
<p>One problem which I've seen recurring in lots of different projects are classes and methods which are quite large. When classes and methods get long, they become difficult to test and maintain. It is easy to make mistakes when working with large classes or methods. In order to be able to work with and test large methods and classes we need to try to break them down into bite sized chunks that will be easy to handle.</p>
<p>The mistake people make when they do this is that they focus on testing the large method or class. We've already established that it isn't easy to test. Since it is not easy to test, we will test it last. How do we get the code where we can test it? We do exactly what I said in the first part of this post. We refactor the code so we can test it. Not the big piece. We pull out small pieces and test them.</p>
<p>We extract methods from our large method and test those pieces. We test them because they're small, bite sized, easy to test, pieces. Sure we don't get the whole method tested yet, but we can do it a piece at a time. As we extract these bits of code the method becomes much easier to read.</p>
<p>If there are now a few methods which have been extracted which seem to perform a similar responsibility we can extract them into a class with a name descriptive of that responsibility. The nice thing is that we now have a class which is easily testable and is tested since we tested each of its methods as we removed them from the large method in the other class.</p>
<p>Now if we're really feeling zealous we could extract an interface from the new class. As a general rule it is better to program against interfaces or abstract classes. The reason for this is that they are easy to test and easy to change when needed. We would then perform a task called dependency injection, which will allow us to use the concrete implementation in our production code and a fake object for our tests. This would then make testing the large method easier.</p>
<p>Even if you don't want to use the interface it is still easier to test the large method once it becomes a lot simpler and its individual pieces need less testing.</p>
<p><img style="border-right: 0px; border-top: 0px; border-left: 0px; border-bottom: 0px" src="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/TheMostImportantRefactorings_8726/ExtractMethods_3.jpg" border="0" alt="ExtractMethods" width="495" height="484" /></p>
