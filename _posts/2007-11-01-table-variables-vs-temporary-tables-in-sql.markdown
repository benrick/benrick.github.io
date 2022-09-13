---
layout: post
title: "Table Variables vs. Temporary Tables in SQL"
date: 2007-11-01 15:44:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Orcs Goblins  and .NET"]
alias: ["/post/Table-Variables-vs-Temporary-Tables-in-SQL", "/post/table-variables-vs-temporary-tables-in-sql"]
---
<!-- more -->
{% include imported_disclaimer.html %}
<p>Temporary tables and table variables can be used in pretty much the same way. One question which is asked, "Which one is better".&nbsp;To answer that it is important to understand a few of the differences between the two. Once we understand how these two types of tables are different we will better understand which we need to use when.</p>
<p>Creating a temporary table is very similar to creating a regular table. In order to do this we use the following code</p>
<div class="csharpcode">
<div style="font-size: 8pt; margin: 20px 0px 10px; overflow: auto; width: 97.5%; cursor: text; max-height: 200px; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border: gray 1px solid; padding: 4px;">
<div style="font-size: 8pt; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;">
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: white; border-style: none; padding: 0px;"><span style="color:#0000ff;">create</span> <span style="color:#0000ff;">table</span> #myTempTable (columnA typeA, columnB typeB, ...)</pre>
</div>
</div>
<p>Table variables are created as regular variables are declared. The type of the variable is just defined as a table.</p>
</div>
<div style="font-size: 8pt; margin: 20px 0px 10px; overflow: auto; width: 97.5%; cursor: text; max-height: 200px; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border: gray 1px solid; padding: 4px;">
<div style="font-size: 8pt; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;">
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: white; border-style: none; padding: 0px;"><span style="color:#0000ff;">declare</span> @myTableVariable <span style="color:#0000ff;">table</span> (columnA typeA, columnB typeB, ...)</pre>
</div>
</div>
<div class="csharpcode">Scope is another important factor to consider. With a table variable its scope is similar to other variables. A temporary table however does not share this scope, and can even be accessed in a stored procedure called by your code. This is one very nice feature of temporary tables over table variables.</div>
<p>Table variables do not record any entries in transaction logs. Temporary tables do store their transactions. Depending on what you are trying to accomplish this can be a benefit for either of the two types of tables. It is often very important to keep track of the transaction log, and in these instances a temporary table is far better for your needs, but other times the transaction log is simply unnecessary and a table variable would be the optimal choice.</p>
<p>I've heard of great performance gains in temporary tables because of their ability to be pre-compiled. I've also heard that table variables are faster than temporary tables in general. I believe this has to do with the nicely defined scope of table variables. Because of this they may use fewer resources than temporary tables. An example of this is the transaction log I mentioned earlier.</p>
<p>For the most part a table variable is just as flexible as a temporary table, and in most instances it also out performs temporary tables in my experience.</p>
<p>One thing to watch out for when using temporary tables is the possibility of causing your store procedure to recompile. Microsoft has a Knowledge Base Article about <a href="http://support.microsoft.com/kb/243586/EN-US/" target="_blank">Troubleshooting stored procedure recompilation</a> which discusses this danger. Table variables will not cause this problem.</p>
<p>I would recommend the use of table variables for everyday use, and only using temporary tables when they're required. Instances of this include the need for a transaction log. Or any time you feel like writing extra lines of code simply to perform cleanup on your temporary table. But that is just my $0.02 on this issue.</p>
<p>Happy SQL writing!</p>
