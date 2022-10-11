---
layout: post
title: "Combining Object Oriented Principles, Practices, and Patterns"
date: 2010-08-01 15:00:00 -0400
comments: true
published: true
categories: ["Archive"]
tags: ["OOP"]
permalink: "/post/Combining-Object-Oriented-Principles-Practices-and-Patterns/"
---

<p>Now that the dust has settled from the recent Software Engineering 101 event we put on in Cleveland, I figured I would repost some of the material I talked about. This means some of connections that I vocalized and supplement the material from the <a href="/post/software-engineering-101-cleveland-slides-and-demos.aspx" target="_blank">slides I used for Software Engineering 101</a>.</p>
<h3>Object Oriented Principles, Practices, and Patterns</h3>
<p>My first talk of the day was on Object Oriented Principles, Practices, and Patterns in which I start by discussing some common principles of object oriented programming: abstraction, encapsulation, inheritance, polymorphism, and I added composition in for good measure, which of course isn&rsquo;t on its own a principle, but I feel deserves to be mentioned as its own entity at that point.</p>
<p>I covered an assortment of good practices for software developers to follow. Since Steve Smith was following my talk with one on SOLID, so I didn&rsquo;t take the opportunity to discuss the Open/Closed Principle, which states that your code should be open to extension and closed to modification. This means that you can add to the behavior of your code by adding new code and not modifying what you already have.</p>
<p>In my patterns section I covered two of my favorite design patterns: the Strategy Pattern and the Template Method Pattern. These two are great for discussing with people. They&rsquo;re very similar yet very different; one encapsulates the structure of an algorithm and allows for modification of the details of the steps while the other focuses on allowing for different algorithms to be used interchangeably. Each uses polymorphism, abstraction, encapsulation, and inheritance. They&rsquo;re simple to explain and demonstrate, and they&rsquo;re also very powerful. This makes them great examples.</p>
<p>&nbsp;</p>
<h3>Combining Everything</h3>
<p>When we combine these principles and some design patterns we can achieve some great things. The strategy pattern is one of my favorite patterns, because it is very useful and improves maintainability greatly. I use it often. It uses, abstraction, encapsulation, composition, polymorphism, and either inheritance or interface implementation. On top of that it also helps follow the Open/Closed Principle, increasing the ease for changing the behavior of an application when the requirements change.</p>
<p>In my talk I was asked a great question, &ldquo;if I don&rsquo;t know design patterns, how will I know what I don&rsquo;t know.&rdquo; In other words, how can you possibly select the correct design problem to solve a problem. I recommended reading learning plenty just so you&rsquo;ll be more prepared. There are plenty of books, and you don&rsquo;t always need &ldquo;the best&rdquo; solution. Usually a good solution to the problem is enough. <a href="http://stevesmithblog.com/" target="_blank">Steve Smith</a> chimed in with a great answer though, he suggested practicing <a href="http://hudsonsc.com/resources/katas/" target="_blank">coding katas</a>, which will often solve problems using design patterns or at least good, worthwhile practices.</p>
