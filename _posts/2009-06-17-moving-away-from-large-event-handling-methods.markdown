---
layout: post
title: "Moving Away From Large Event Handling Methods"
date: 2009-06-17 09:34:00 -0400
comments: true
published: true
categories: ["Archive"]
tags: ["C#"]
permalink: "/post/Moving-Away-From-Large-Event-Handling-Methods/"
---

<p>A big issue which can be seen when looking at a lot of ASP.NET code is the classic "do everything" method. This is often some kind of an event handler. It is sometimes one for the page such as with Page Load. Other times it is a control on that page that owns the event. Either way this is a nasty piece of code whether you're testing or not.</p>
<p>These dangerous pieces of muck are difficult to work with, and I'll say they scare the crap out of me when I need to work with them. So I am sure everyone knows why they are difficult in general to work with. Obviously there is a lot of code there in one place doing a lot of different stuff.</p>
<p>When we think about what might be in one such method we come up with a lot of nasty stuff.</p>
<p><span style="text-decoration: underline;">Nasty Stuff Sometimes Found in Large Event Handlers</span> (Some of these are much worse than others)</p>
<ul>
<li>Business Rules Logic</li>
<li>Dependencies on page controls and their properties</li>
<li>Knowledge of the underlying data persistence layer</li>
<li>Dependencies on the server context</li>
<li>Dependencies on configuration information</li>
<li>Complicated UI logic determining how the page should be rendered</li>
</ul>
<p>So I am sure I've missed some other really nasty thing which could have been in this method. As with any large method this is obviously violating the <a href="http://en.wikipedia.org/wiki/Single_responsibility_principle" target="_blank">Single Responsibility Principle</a>. For the sake of this blog post I am going to define the method we are talking about as a click handling event for a save button on a web form.</p>
<p>So obviously we should extract a method from this to get the "Complicated UI logic determining how the page should be rendered" into a method which has anything to do with UI logic. Since we are on the page, we can keep the UI logic here. This is the UI layer after all.</p>
<p>Running through each of these and getting them into the <em>right</em> place could take us a while, so I'll just be covering a couple of them here.</p>
<h3>Removing the Dependency on the Data Persistence</h3>
<p>This is one of the most important steps we can take to improve our code quality. Removing the database dependency will assist us in keeping our concerns separated and shrinking the size of this monster method. By removing this dependency we are better able to test this code. We want to make sure that we are coding against an interface giving us access to the data we need. This will allow us to remove the dependency on our data when we are testing.</p>
<p>I don't care exactly how you do it, but this needs to be broke apart. I generally use the word "Repository" when referring to a class that will get and store my data. I like this word because it is a non-specific word meaning that it is a persistence class. There are a lot of implementations of repositories. If you want to learn more then read about <a href="http://lmgtfy.com/?q=repository+pattern" target="_blank">repositories on Google</a>. A lot of <a href="http://ayende.com/Blog/Default.aspx" target="_blank">very</a> <a href="http://martinfowler.com/" target="_blank">smart</a> people have written things <a href="http://www.martinfowler.com/eaaCatalog/repository.html" target="_blank">for</a> and <a href="http://ayende.com/Blog/archive/2009/04/17/repository-is-the-new-singleton.aspx" target="_blank">against</a> the repository pattern.</p>
<p>We want to use this pattern because the data accessing code and the persistence layer can be moved into the repository. This lets us remove that code from the nasty method.</p>
<p>When we write tests we will use a mock, fake, or stubbed version of the repository so we don't have to maintain a database.</p>
<h3>Removing the Dependency on the Web</h3>
<p>Since we are working with web forms here we have a strong dependency on our web form when we are in the event handler in the code behind of our page. In ASP.NET MVC this is not as much of an issue. A lot of people don't realize that a lot of the stuff that makes MVC so nice is that it is actually just helping to guide us towards a lot of these principles and rules we already tried to follow. This separation and everything is right out of the Single Responsibility Principle.</p>
<p>When we are breaking apart our code we want to have a lot of small interconnected pieces of code working together to achieve something great. However to get to that point we should be moving in small steps. One of the best ones in this circumstance is to pull as much of the logic as possible away from the web form.</p>
<p>To achieve this separation we will create a class we will call a "controller". If we make the class WebForm1Controller we can put a method in there that handles this event for us. It will, however, take in the <em>values</em> it needs from the Controls instead of having access to the controls itself. It can also take in any values it needs from the HttpContext or anything else. The point of this is that this code in the controller can run <em>without</em> actually having the web portion of your code. (THIS LETS YOU TEST IT!)</p>
<p>So you might be thinking at this point that all we have done is moved the code. Well sort of. What we did was <em>limit our dependency on the web.</em> We did this by making sure that all we needed was the values. You are right that we could have kept this as a separate method in the code behind. The difference is that in this new class <em>we do not even have access to the controls so no one can try to directly access them from here. We are also more easily able to create instances of this class. The one associated with a web form has a lot more red tape to deal with than our freshly created controller class.</em></p>
<p>You might now ask if we are done fixing this code. Certainly not. We have much more to do, but the code is <em>better</em>. As I've said before, it is a <a href="/post/Writing-Clean-Code-is-a-Process/" target="_blank">lengthy process to write better code</a>. If you're not working towards writing better code every time you write code, you're probably making code worse. Try making one thing cleaner, nicer, more concise every time you're working with the code. Even if you're just extracting a small method or renaming something, you're making things better. Don't be discouraged if you can't do a large refactoring in one sitting. Notice here that we aren't done, but we've made the code a lot better. In fact, I bet we could test the controller's business logic now.</p>
