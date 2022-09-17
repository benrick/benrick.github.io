---
layout: post
title: "Exploring IronPython"
date: 2007-11-27 16:23:00 -0500
comments: true
published: true
categories: ["blog", "Archive"]
tags: ["Blog"]
permalink: "/post/Exploring-IronPython/"
---
<!-- more -->



<p>&nbsp;<img src="http://upload.wikimedia.org/wikipedia/en/2/25/PythonProgLogo.png" alt="" width="174" height="48" align="right" /> Earlier today I downloaded IronPython, and I've tested it out a little bit. The command line interpreter is nice and works pretty painlessly whether you are compiling the source or just executing the binaries. Python is a great language IMHO. Just like every language that has ever been written, it has a few problems. Python emphasizes short readable code.</p>
<p>IronPython's interpreter, <em>ipy</em>, allows interactive sessions as well as execution of files. It acts very similarly to Python's Official interpreter, <em>IDLE</em>. This makes transitioning easy for someone who already knows how to program using the Python language.</p>
<p>I sat down and took a couple of seconds writing a simple fibonacci number program to print out the first 10 fibonacci numbers as an example of how Python code is used.</p>
<p>&nbsp;</p>
<pre>def fib(number):
    if number == 0:
        return 0
    elif number == 1:
        return 1
    else:
        return fib(number-1) + fib(number-2)

def main():
    for i in range(10):
        print fib(i)

main()
</pre>
<p>&nbsp;</p>
<p>If this code is in the file <em>fib.py</em> I can execute it using the following command.</p>
<p><em>ipy fib.py</em></p>
<p>It generates the following output.</p>
<p>&nbsp;</p>
<pre>0
1
1
2
3
5
8
13
21
34
</pre>
<p>People have integrated IronPython into Visual Studio as well, and I'll soon look into doing that as well. I like how simply and easily I am able to create this little program. Now with IronPython I also have access to the .NET Framework's libraries.</p>
