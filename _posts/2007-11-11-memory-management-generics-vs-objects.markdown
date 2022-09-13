---
layout: post
title: "Memory Management: Generics vs objects"
date: 2007-11-11 20:15:00 -0500
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Orcs Goblins  and .NET"]
permalink: "/post/Memory-Management-Generics-vs-objects"
---
<!-- more -->

<p>One of the most important parts of software development is memory management. Memory management is important for every software&nbsp;application. If one is to write a well developed software application, one must have a fair bit of knowledge in the area of memory managament. It is important to understand the underlying technology which allows programs to function. There are many aspects of programs which come into play often in .NET applications; variables, functions, garbage collection.</p>
<p><strong>Understanding Garbage Collection, Heaps, and Stacks</strong></p>
<p>When using a language with a heap, it is important to understand that memory will be allocated dynamically. This is separate from where the basic program memory resides; the stack. On the stack memory builds as the program executes. Local variables are stored with the function information. This is the memory used in pretty much every language. When a heap is involved there is basically an area of memory where variables may be dynamically defined and only references to these variables are stored as pointers on the stack.</p>
<p>When the variable is out of scope or removed it is merely the reference to the variable which is removed. A garbage collector will come by later to free the memory for later use. Whenever there is not enough room to allocate memory in the heap the garbage collector wil come and clear unused memory.</p>
<p><strong>Understanding Variable Types</strong></p>
<p>There are basically two types of variables; value and reference. The value types tend to be the simpler&nbsp;variables and the reference types tend to be the more advanced variables. Some examples of value types are enums, ints, doubles, bools,&nbsp;chars, and structs. Some reference types are arrays, lists, and classes. The value types are the ones stored locally with the stack and the reference types are stored in the heap, and a reference to them is stored on the stack. When using the&nbsp;<em>new</em> keyword, memory is allocated on the heap and a referenced object&nbsp;is created.</p>
<p><strong>Passing Parameters to Functions.</strong></p>
<p>When passing variables as parameters to functions, it is important to understand the two main ways in which these variables may be passed. Variables may be passed by reference or by value. Passing by value means that we make a copy of the local variable and use that in the function. This means that our value type variable will be copied and if we use a reference type it means that only the reference will be copied. This means that we will still be accessing the same location in the heap even if we pass by value. By using the <em>ref</em> keyword you may pass a parameter by reference. This means for a value type you are able to just pass a reference to the original value. Do not pass a reference type by reference, because it will just make a reference to the reference to the value and that will slow things down for no reason. Passing by reference is a good idea if the value is large, so with a large struct you may want to pass by reference instead of copying all of the data.</p>
<p><strong>Generics vs. Objects</strong></p>
<p>When using parameters of type object, <a href="http://en.wikipedia.org/wiki/Object_type" target="_blank">boxing and unboxing</a> is used to take the variable and changing it to and from object. This seems pretty easy because one can simply add <em>(object) </em>when passing the parameter. The problem here is that this will create a new instance of an object. This means we will be making a copy of the variable instead of just using a reference to the variable. This will take time, and will also allocate extra memory which will need to be collected by the garbage collector later. This will also decrease the performance of our program. This is why it is important to use generics to prevent this performance hit. When we use generics we do not have to make a copy of the value, we merely pass a reference to the original value.</p>
<p>Be careful, and try to use Generics whenever possible. Your memory will thank you.</p>
