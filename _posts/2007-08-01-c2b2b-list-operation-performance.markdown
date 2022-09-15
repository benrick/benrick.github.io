---
layout: post
title: "C++ List Operation Performance"
date: 2007-08-01 15:36:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Orcs Goblins  and .NET"]
permalink: "/post/C2b2b-List-Operation-Performance/"
---
<!-- more -->

<p>I am fairly certain that the C++ Standard Template Library's list object's size function is an O(n) operation. For those of you less algorithmically informed people I am saying that a linked list which uses pointers to the next object in the list has to take linear time (directly corresponding to the number of elements) to find out the size of the list. At first this seems kind of odd. One would wonder why not just keep the count of the elements stored somewhere.</p>
<p>Keeping the count of the number of elements in a linked list will make what I believe is the linked list's greatest asset less valuable. The splice function (which is like the AddRange function) is able to just update pointers. This is amazingly useful because added n number of elements can take constant time. Meaning that it takes just as long to add 10 elements as to add 1000 elements. When needed that is a life saver. Having that ability though prevents being able to keep track of the size of the list, because the list doesn't know how many elements you are splicing in. It would need to take linear time to count them. Because of this it would make it linear instead of constant time. Ouch.</p>
<p>Because of this close relationship between the size and splice functions one will have to be linear and one constant. It seems that it was decided that with a linked list it would just be easier to iterate to the end instead of using the size. Splicing is a lot more important in my opinion to the usefulness of a linked list. I suggest perhaps a second object which is a linked list which has a constant size and a linear splice for when size will be checked more often than splicing will occur. &nbsp;</p>
<p>I was discussing this with someone recently and found it quite interesting, and I now think I am going to go and start reading more about the algorithms of the functions used in C#. Perhaps in the future I will write about the algorithms in .NET and the runtime of these algorithms. I hope so.</p>
