---
layout: post
title: "Understanding the Stack Data Structure"
date: 2007-10-05 15:30:00 -0400
comments: true
published: true
categories: ["Archive"]
tags: ["Blog"]
permalink: "/post/Understanding-the-Stack-Data-Structure/"
---
<!-- more -->



<p>I found myself recently explaining a few times how the data structure commonly called a stack works. The technical term for a stack would be a Last in First out Data Structure (LIFO). To practically repeat myself, this means that the last object to go into the structure is the first one which will come out of the structure.</p>
<p>I've heard plenty of interesting analogies for this behavior. All too often I hear this being described as a stack of plates. Plates can be added easily onto the top of the stack, and can be removed from the top of the stack easily. Working with any plates not on the top is difficult because there are other plates on top of them. This is basically how a stack works.</p>
<p>While explaining the push() and pop() methods of stacks, I came up with an analogy which I think is far more interesting. To my students I described the stack as a Pez&nbsp;dispenser. You load the dispenser from the top and unload it from the top.</p>
<p><img src="http://static.flickr.com/1159/1490354572_ec75a14755.jpg" border="0" alt="PezAnalogy" /></p>
<p>When you get a candy from the dispenser it comes out of the top and you now have possession of it. With a stack you get the value from the top and you now have possession of it. When adding candy to the dispenser you will add it on top of any existing candy. With a stack you will add new values on top of the existing values.</p>
<p>One extra method available to a Stack is the ability to "peek" at the top value without removing it. This is often necessary when using a stack, and also in a Pez dispenser. When you lift the head of the dispenser a little bit you can peek in to check what color is on top. If it is not one you like, you can still close the dispenser without having removed the candy. The same can be done with a stack.</p>
<p><strong>Basic Implementation</strong></p>
<p>Stacks may be implemented easily with an array or a linked-list as the underlying data structures. When drawing a stack it is far more common to draw the array version. There is one pointer of importance with a stack. This pointer is usually called the "top" pointer. It is a pointer which updates every time a "push" or a "pop" occurs, because this pointer will always point to the top of the stack. This is the pointer used to get to the stack and work with it.</p>
<p>The Push and Pop Operations work as the following image shows.</p>
<p><img src="http://static.flickr.com/1350/1490540282_c96252968c.jpg" border="0" alt="StackOperations" /></p>
<p>&nbsp;</p>
<p>Enjoy, and look forward to more blog posts explaining interesting Computer Science topics.</p>
