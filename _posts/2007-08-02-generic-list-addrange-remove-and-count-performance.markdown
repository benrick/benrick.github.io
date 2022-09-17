---
layout: post
title: "Generic List AddRange, Remove, and Count Performance"
date: 2007-08-02 14:00:00 -0400
comments: true
published: true
categories: ["blog", "Archive"]
tags: ["Blog"]
permalink: "/post/Generic-List-AddRange-Remove-and-Count-Performance/"
---
<!-- more -->



<p>The .NET System.Collections.Generic.List class is not a <a href="http://en.wikipedia.org/wiki/Linked_list">linked list</a> as non-.NET users might expect. This list class is actually more like an array list than a linked list. Because of this it has some of the benefits of arrays. Simply because of the array data structure which exists within the generic list class, the class is able to achieve a constant time Count function. The basic array data structure is a collection of objects which are stored contiguously in memory, and because of this it makes counting them easy. It also makes it quite easy to index into a specific location, because you can just jump straight to the correct location in memory. With a linked list one has to traverse the list. The advantage of the linked list is that it is held together using pointers, so if you want to add nodes it is simply an update to pointers. This means that adding a collection of nodes can take constant time.</p>
<p>I would highly recommend against the array list if you will be adding and removing objects from this collection often. Since there is an allocated amount of space in memory for the array this means that if you need to exceed this space then you will need to create a new list. Using <a href="http://en.wikipedia.org/wiki/Big_O_notation">Big O notation</a> the AddRange function of list will take O(n) time to complete. The n in this case is the number of elements to add. This doesn't seem to bad, but when the allotted space is exceeded the array will need to move and recreate itself with more space. This is the big performance hit. For this operation it will have O(n+m) time, because you will have to do the regular n operations plus m operations for the original data in the array.</p>
<p>Removing an element from an array requires a little bit of work. One reason for this is that the array data structure should never contain an empty space. This means that first you will need to perform a linear search algorithm to find the element to remove. Stepping one by one through the list. Upon reaching the element to remove, it is removed, but then all the elements after that one must be moved forward in the array so no space exists. This causes the remove function to perform in linear time.</p>
<ul>
<li>Capacity O(1)</li>
<li>Count O(1)</li>
<li>AddRange O(n) or O(n+m)</li>
<li>Remove O(n) </li>
</ul>
<p>I am planning to write of series of little bits of stuff. If you catch any mistakes in any of this series please comment on the correction ASAP. I don't want to be passing along incorrect information.</p>
<p>Enjoy!&nbsp;</p>
