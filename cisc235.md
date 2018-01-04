
<!DOCTYPE html>
<!--
==============================================================================
           "GitHub HTML5 Pandoc Template" v2.0 — by Tristano Ajmone
==============================================================================
Copyright © Tristano Ajmone, 2017, MIT License (MIT). Project's home:
- https://github.com/tajmone/pandoc-goodies
The CSS in this template reuses source code taken from the following projects:
- GitHub Markdown CSS: Copyright © Sindre Sorhus, MIT License (MIT):
  https://github.com/sindresorhus/github-markdown-css
- Primer CSS: Copyright © 2016-2017 GitHub Inc., MIT License (MIT):
  http://primercss.io/
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
The MIT License
Copyright (c) Tristano Ajmone, 2017 (github.com/tajmone/pandoc-goodies)
Copyright (c) Sindre Sorhus <sindresorhus@gmail.com> (sindresorhus.com)
Copyright (c) 2017 GitHub Inc.
"GitHub Pandoc HTML5 Template" is Copyright (c) Tristano Ajmone, 2017, released
under the MIT License (MIT); it contains readaptations of substantial portions
of the following third party softwares:
(1) "GitHub Markdown CSS", Copyright (c) Sindre Sorhus, MIT License (MIT).
(2) "Primer CSS", Copyright (c) 2016 GitHub Inc., MIT License (MIT).
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:
The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.
THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
==============================================================================-->
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="generator" content="pandoc" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes" />
  <meta name="author" content="Tristano Ajmone (tajmone@gmail.com)" />
  <meta name="dcterms.date" content="2017/11/21" />
  <title>CISC 235: Data Structures</title>
  <style type="text/css">
.markdown-body{-ms-text-size-adjust:100%;-webkit-text-size-adjust:100%;color:#24292e;font-family:-apple-system,system-ui,BlinkMacSystemFont,"Segoe UI",Helvetica,Arial,sans-serif,"Apple Color Emoji","Segoe UI Emoji","Segoe UI Symbol";font-size:16px;line-height:1.5;word-wrap:break-word;box-sizing:border-box;min-width:200px;max-width:980px;margin:0 auto;padding:45px}.markdown-body a{color:#0366d6;background-color:transparent;text-decoration:none;-webkit-text-decoration-skip:objects}.markdown-body a:active,.markdown-body a:hover{outline-width:0}.markdown-body a:hover{text-decoration:underline}.markdown-body a:not([href]){color:inherit;text-decoration:none}.markdown-body strong{font-weight:600}.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6{margin-top:24px;margin-bottom:16px;font-weight:600;line-height:1.25}.markdown-body h1{font-size:2em;margin:.67em 0;padding-bottom:.3em;border-bottom:1px solid #eaecef}.markdown-body h2{padding-bottom:.3em;font-size:1.5em;border-bottom:1px solid #eaecef}.markdown-body h3{font-size:1.25em}.markdown-body h4{font-size:1em}.markdown-body h5{font-size:.875em}.markdown-body h6{font-size:.85em;color:#6a737d}.markdown-body img{border-style:none}.markdown-body svg:not(:root){overflow:hidden}.markdown-body hr{box-sizing:content-box;height:.25em;margin:24px 0;padding:0;overflow:hidden;background-color:#e1e4e8;border:0}.markdown-body hr::before{display:table;content:""}.markdown-body hr::after{display:table;clear:both;content:""}.markdown-body input{margin:0;overflow:visible;font:inherit;font-family:inherit;font-size:inherit;line-height:inherit}.markdown-body [type=checkbox]{box-sizing:border-box;padding:0}.markdown-body *{box-sizing:border-box}.markdown-body blockquote{margin:0}.markdown-body ol,.markdown-body ul{padding-left:2em}.markdown-body ol ol,.markdown-body ul ol{list-style-type:lower-roman}.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul{margin-top:0;margin-bottom:0}.markdown-body ol ol ol,.markdown-body ol ul ol,.markdown-body ul ol ol,.markdown-body ul ul ol{list-style-type:lower-alpha}.markdown-body li>p{margin-top:16px}.markdown-body li+li{margin-top:.25em}.markdown-body dd{margin-left:0}.markdown-body dl{padding:0}.markdown-body dl dt{padding:0;margin-top:16px;font-size:1em;font-style:italic;font-weight:600}.markdown-body dl dd{padding:0 16px;margin-bottom:16px}.markdown-body code{font-family:SFMono-Regular,Consolas,"Liberation Mono",Menlo,Courier,monospace}.markdown-body pre{font:12px SFMono-Regular,Consolas,"Liberation Mono",Menlo,Courier,monospace;word-wrap:normal}.markdown-body blockquote,.markdown-body dl,.markdown-body ol,.markdown-body p,.markdown-body pre,.markdown-body table,.markdown-body ul{margin-top:0;margin-bottom:16px}.markdown-body blockquote{padding:0 1em;color:#6a737d;border-left:.25em solid #dfe2e5}.markdown-body blockquote>:first-child{margin-top:0}.markdown-body blockquote>:last-child{margin-bottom:0}.markdown-body table{display:block;width:100%;overflow:auto;border-spacing:0;border-collapse:collapse}.markdown-body table th{font-weight:600}.markdown-body table td,.markdown-body table th{padding:6px 13px;border:1px solid #dfe2e5}.markdown-body table tr{background-color:#fff;border-top:1px solid #c6cbd1}.markdown-body table tr:nth-child(2n){background-color:#f6f8fa}.markdown-body img{max-width:100%;box-sizing:content-box;background-color:#fff}.markdown-body code{padding:.2em 0;margin:0;font-size:85%;background-color:rgba(27,31,35,.05);border-radius:3px}.markdown-body code::after,.markdown-body code::before{letter-spacing:-.2em;content:"\00a0"}.markdown-body pre>code{padding:0;margin:0;font-size:100%;word-break:normal;white-space:pre;background:0 0;border:0}.markdown-body .highlight{margin-bottom:16px}.markdown-body .highlight pre{margin-bottom:0;word-break:normal}.markdown-body .highlight pre,.markdown-body pre{padding:16px;overflow:auto;font-size:85%;line-height:1.45;background-color:#f6f8fa;border-radius:3px}.markdown-body pre code{display:inline;max-width:auto;padding:0;margin:0;overflow:visible;line-height:inherit;word-wrap:normal;background-color:transparent;border:0}.markdown-body pre code::after,.markdown-body pre code::before{content:normal}.markdown-body .full-commit .btn-outline:not(:disabled):hover{color:#005cc5;border-color:#005cc5}.markdown-body kbd{box-shadow:inset 0 -1px 0 #959da5;display:inline-block;padding:3px 5px;font:11px/10px SFMono-Regular,Consolas,"Liberation Mono",Menlo,Courier,monospace;color:#444d56;vertical-align:middle;background-color:#fcfcfc;border:1px solid #c6cbd1;border-bottom-color:#959da5;border-radius:3px;box-shadow:inset 0 -1px 0 #959da5}.markdown-body :checked+.radio-label{position:relative;z-index:1;border-color:#0366d6}.markdown-body .task-list-item{list-style-type:none}.markdown-body .task-list-item+.task-list-item{margin-top:3px}.markdown-body .task-list-item input{margin:0 .2em .25em -1.6em;vertical-align:middle}.markdown-body::before{display:table;content:""}.markdown-body::after{display:table;clear:both;content:""}.markdown-body>:first-child{margin-top:0!important}.markdown-body>:last-child{margin-bottom:0!important}.Alert,.Error,.Note,.Success,.Warning{padding:11px;margin-bottom:24px;border-style:solid;border-width:1px;border-radius:4px}.Alert p,.Error p,.Note p,.Success p,.Warning p{margin-top:0}.Alert p:last-child,.Error p:last-child,.Note p:last-child,.Success p:last-child,.Warning p:last-child{margin-bottom:0}.Alert{color:#246;background-color:#e2eef9;border-color:#bac6d3}.Warning{color:#4c4a42;background-color:#fff9ea;border-color:#dfd8c2}.Error{color:#911;background-color:#fcdede;border-color:#d2b2b2}.Success{color:#22662c;background-color:#e2f9e5;border-color:#bad3be}.Note{color:#2f363d;background-color:#f6f8fa;border-color:#d5d8da}.Alert h1,.Alert h2,.Alert h3,.Alert h4,.Alert h5,.Alert h6{color:#246;margin-bottom:0}.Warning h1,.Warning h2,.Warning h3,.Warning h4,.Warning h5,.Warning h6{color:#4c4a42;margin-bottom:0}.Error h1,.Error h2,.Error h3,.Error h4,.Error h5,.Error h6{color:#911;margin-bottom:0}.Success h1,.Success h2,.Success h3,.Success h4,.Success h5,.Success h6{color:#22662c;margin-bottom:0}.Note h1,.Note h2,.Note h3,.Note h4,.Note h5,.Note h6{color:#2f363d;margin-bottom:0}.Alert h1:first-child,.Alert h2:first-child,.Alert h3:first-child,.Alert h4:first-child,.Alert h5:first-child,.Alert h6:first-child,.Error h1:first-child,.Error h2:first-child,.Error h3:first-child,.Error h4:first-child,.Error h5:first-child,.Error h6:first-child,.Note h1:first-child,.Note h2:first-child,.Note h3:first-child,.Note h4:first-child,.Note h5:first-child,.Note h6:first-child,.Success h1:first-child,.Success h2:first-child,.Success h3:first-child,.Success h4:first-child,.Success h5:first-child,.Success h6:first-child,.Warning h1:first-child,.Warning h2:first-child,.Warning h3:first-child,.Warning h4:first-child,.Warning h5:first-child,.Warning h6:first-child{margin-top:0}h1.title,p.subtitle{text-align:center}h1.title.followed-by-subtitle{margin-bottom:0}p.subtitle{font-size:1.5em;font-weight:600;line-height:1.25;margin-top:0;margin-bottom:16px;padding-bottom:.3em}div.line-block{white-space:pre-line}
  </style>
  <style type="text/css">code{white-space: pre;}</style>
  <style type="text/css">
div.sourceLine, a.sourceLine { display: inline-block; min-height: 1.25em; }
a.sourceLine { pointer-events: none; color: inherit; text-decoration: inherit; }
.sourceCode { overflow: visible; }
code.sourceCode { white-space: pre; }
@media print {
code.sourceCode { white-space: pre-wrap; }
div.sourceLine, a.sourceLine { text-indent: -1em; padding-left: 1em; }
}
pre.numberSource div.sourceLine, .numberSource a.sourceLine
  { position: relative; }
pre.numberSource div.sourceLine::before, .numberSource a.sourceLine::before
  { content: attr(data-line-number);
    position: absolute; left: -5em; text-align: right; vertical-align: baseline;
    border: none; pointer-events: all;
    -webkit-touch-callout: none; -webkit-user-select: none;
    -khtml-user-select: none; -moz-user-select: none;
    -ms-user-select: none; user-select: none;
    padding: 0 4px; width: 4em; }
pre.numberSource { margin-left: 3em; border-left: 1px solid #aaaaaa; color: #aaaaaa;  padding-left: 4px; }
@media screen {
a.sourceLine::before { text-decoration: underline; color: initial; }
}
code span.kw { color: #0000ff; } /* Keyword */
code span.ch { color: #008080; } /* Char */
code span.st { color: #008080; } /* String */
code span.co { color: #008000; } /* Comment */
code span.ot { color: #ff4000; } /* Other */
code span.al { color: #ff0000; } /* Alert */
code span.er { color: #ff0000; font-weight: bold; } /* Error */
code span.wa { color: #008000; font-weight: bold; } /* Warning */
code span.cn { } /* Constant */
code span.sc { color: #008080; } /* SpecialChar */
code span.vs { color: #008080; } /* VerbatimString */
code span.ss { color: #008080; } /* SpecialString */
code span.im { } /* Import */
code span.va { } /* Variable */
code span.cf { color: #0000ff; } /* ControlFlow */
code span.op { } /* Operator */
code span.bu { } /* BuiltIn */
code span.ex { } /* Extension */
code span.pp { color: #ff4000; } /* Preprocessor */
code span.do { color: #008000; } /* Documentation */
code span.an { color: #008000; } /* Annotation */
code span.cv { color: #008000; } /* CommentVar */
code span.at { } /* Attribute */
code span.in { color: #008000; } /* Information */
  </style>
  <!--[if lt IE 9]>
    <script src="//cdnjs.cloudflare.com/ajax/libs/html5shiv/3.7.3/html5shiv-printshiv.min.js"></script>
  <![endif]-->
</head>
<body>
<article class="markdown-body">
<header>
<h1 class="title followed-by-subtitle">CISC 235: Data Structures</h1>
<div class="summary">
<p></p>
<p>This course covers topics ranging from algorithmic complexity, stacks and queues, heaps, sorting algorithms, BSTs and its various types, and more. I'll be updating it throughout the course!</p>
</div>
</header>
<nav id="TOC">
<h1 class="toc-title">Topics</h1>

<ul>
<li><a href="#algorithmic-complexity">Algorithmic Complexity</a></li>
<li><a href="#stacks-queues-heaps">Stacks, Queues, and Heaps</a></li>
<li><a href="#bsts">Binary Search Trees</a></li>
<li><a href="#hashing">Hashing</a></li>

<li><a href="#sorting">Sorting Algorithms</a><ul>
<li><a href="#insertion-sort">Insertion Sort</a></li>
<li><a href="#merge-sort">Merge Sort</a></li>
<li><a href="#quick-sort">Quick Sort</a></li>
<li><a href="#heap-sort">Heap Sort</a></li>
</ul></li>

<li><a href="#graphs">Graphs</a><ul>
<li><a href="#bfs">Breadth First Search</a></li>
<li><a href="#dfs">Depth First Search</a></li>
<li><a href="#minspantrees">Minimum Spanning Trees</a></li>
</ul></li>

<li><a href="#disjoint-sets">Disjoint Sets</a></li>

<li><a href="#shortest-paths">Shortest Paths</a><ul>
<li><a href="#dijkstra">Dijkstra</a></li>
<li><a href="#bell-ford">Bellman-Ford</a></li>
<li><a href="#extra-paths">Extras</a></li>
</ul></li>

</ul>

</nav>
<hr>
<h1 id="algorithmic-complexity">Algorithmic Complexity</h1>


<h3>Data structures are a smart way of organizing data, based on which we can develop efficient algorithms easily</h3>

<ul>
<li>They're a way of storing and organizing data to facilitate access and modifications</li>
<li>We learn the strength and limitations of each data structure so that we know which one to use!</li>
</ul>

<h3>Analysis:</h3>

<ul><li>Looking at worst-case, average-case, amortized, and expected worst-case for randomized algorithms</li>
<li>This is more important than algorithms, but less fun to learn :')</li></ul>

<h4>Abstract Data Types (ADTs) and Data Structures: Two related <strong>but</strong> different concepts.</h4>

<p>ADT: describes <strong>what</strong> (the interface)</p>
  <ul><li>what data is stored</li>
  <li>what operation is supported</li></ul>
<p>Data structure: describes <strong>how</strong> (the implementation)</p>
  <ul><li>how the data is stored</li>
  <li>how to perform the operations</li></ul>

<p><strong>Complexity</strong> is the amount of resource required by an algorithm, measured as a function of the input size. Complexity can be split into two types:</p>

<ul><li>time complexity: <strong>number of steps</strong> (running time) executed by an algorithm</li>
  <li>space complexity: <strong>number of units of space</strong> required by an algorithm<ul></li>
  <li>i.e. the number of elements in a list, the number of nodes in a tree/graph, etc.</li></ul>
</ul>

```
Example: Search a linked list.

    SearchFortyTwo(L):
      z = L.head     // z is pointing at the linked list's first element
      while z != None and z.key != 42
        z = z.next   // while neither of the above conditions are met, z will increment along L
      return z
```

<p>So let L = 41 -> 51 -> 12 -> 42 -> 20 -> 88. How many times will line 2 be executed?</p>
Since the z.key = 42 case is true after the z has been compared 4 times, line 2 will be executed **4 times**!
*Now let L = 41 -> 51 -> 12 -> 24 -> 20 -> 88. How many times will line 2 be executed?*
**7 times!** The first case (z = None) is true when z is pointed at the last node.
Analysis: Best-case, Worst-case, Average-case

1. **Worst Case Running time**: What is the maximum (longest) running time for some input of size *n*?

Let t(x) be the *running time* of an algorithm A with input of size x.
T(n) = max {t(x): x is an input of size n}

1. **Best Case Running time**: Not very interesting, rarely studied. We should prepare for the worst, not the best!

T(n) = max {t(x): x is an input of size n}

1. **Average Case Running time**: The reality is, running time is "distributed" between the best and worst cases. So for our search linked list example, the running time is distributed between 1 and n + 1. The average case is the **expectation** of the running time. Let t_n be a random discrete variable whose possible values are between 1 and n + 1. The expectation would be

summation from best to worst case of t multiplied with the P(t_n = t)
hold on! to take the expectation of a r.v., we need its pmf (which we get from its distribution)
Example: What is the worst case running time among all possible linked lists L with length n?

- This would be the case where no node is 42 (42 is not in L). So, T(n) = n + 1 (max number of steps to compare all nodes plus a final none).

Asymptotic: Upper, tight, and lower bounds:

1. O(f(n)) is the set of functions that grow *no faster* than f(n). If g is an element of O(f(n)), then we can say that g is asymptotically *upper bounded by f(n)* (g cannot grow faster than f(n)).
2. Omega(f(n)) is the set of functions that grow *no slower* than f(n). If g is an element of Omega(f(n)), then we can say that g is asymptotically *lower bounded by f(n)* (g cannot grow slower than f(n)).
3. If g is an element of O(f(n)) and Omega(f(n)), then g is an element of the tight bound of f(n), where the tight bound is the set of functions that grow no slower or faster than f(n).

Ideas behind Asymptotic Notations:

- We only care about the **rate** of growth, so constant factors don't matter
- We only care about **large inputs**, so only the highest degree term matters

Growth rate ranking (slow --> fast): f(n) = 1 --> logn --> sqrt(n) --> n --> nlogn --> n^2 --> n^3 --> 2^n --> n^n
High level look at asymptotic notations:

- it is a **simplification**(!!) of the 'real' running time. In the real world, constant factor matters! Hardware matters! Implementation matters!
- simplification allows the development of the theory of computational complexity (an entire subfield of cs)

**Combining Best/Avg/Worst and Asymptotic**: O and Omega can BOTH be used to upper and lower bound worst/best/average running time.
Example: Commuting time to school from home case:
**1.** "Even the **worst** day is *less than 2 hours*". So _everyday_ is less than 2 hours. This is the upper bound on the worst case for commuting.
(!) Equivalently, *how do you argue that some algorithm A(x)'s worst case running time is in O(n^2)?*
First, let's deconstruct the question. Worst case is the longest running time for some input of size n. Big O is the set of functions that grow no faster than f(n) (i.e., the upper bound, and in this case, cn^2). So, the question is asking, how do we know that the running time is no larger than cn^2?
We can check for every input x of size n, the running time of the algorithm A with input x is no larger than cn^2, where c > 0 and a constant.
**2.** "The **worst** day is *more than 2 hours*". So there is no day where the commute is less than 2 hours. This is the lower bound on the best case for commuting.
(!) Equivalently, *how do you argue that some algorithm A(x)'s best case running time is in Omega(n^2)?*
The best case is the shortest running time of an algorithm for some input x of size n. Omega is the set of functions that grow no slower than f(n) (in this case, cn^2). So, the question is asking, how do we know that the shortest running time is no less than cn^2?
We can check for every input x of size n, the running time of the algorithm A with input x is no less than cn^2, where c > 0 and a constant.

----------

**Lecture 2: Queues and Heaps**
This week, we're looking at the abstract data type called 'queue' and the heap data structure.
Queue: first in, first serve. A queue is a collection of elements with the supported operations **enqueue(Q,x), dequeue(Q), and peekfront(Q)**.
Max-Priority Queue: a collection of elements **with priorities**, i.e., each element x has k priority. (ex: oldest person is served first). It has the supported operations **insert(Q,x), ExtractMax(Q), Max(Q), and IncreasePriority(Q,x,k) which increases x's priority to k**.
The applications of Priority Queues include job scheduling in operating systems (processes have different priorities), bandwidth management in a router, finding the minimum spanning tree of a graph, etc.
Implement a Max-Priority Queue
Using an unsorted linked list,
**Insert(Q,x)** : x is a node. Insert x at the head, which has the tight bound of 1.
**IncreasePriority(Q,x,k)** : Change x's priority to k, which has the tight bound of 1.
**Max(Q)** : Have to go through the whole list, which has the tight bound of n.
**ExtractMax(Q)** : Go through the whole list to find x with max priority (O(n)), then delete it (O(1) if double linked) and return it, so overall it has a tight bound of n.
Using a sorted and unsorted linked list both give us pretty bad tight bounds of n for some operations, and that does not scale well for very large inputs. Is there a better way to link these elements?
... Yes! We can use a heap!
**Heap**: A heap is a **binary heap** stored in an array, which is a binary tree
**Binary Max-Heap**: A binary max-heap is a *nearly-complete* binary tree that has the *max-heap property*. A binary tree has at most 2 children for each node. A nearly-complete binary tree means that every level is completely filled except for the bottom level, where nodes are filled to as *far left* as possible.
Why is it important for it to be a nearly-complete binary tree?
1. Because we can then store the tree in an array, and each node knows which index has its parent or left/right child.
LeftChild(index) = 2*index
RightChild(index) = 2(index) + 1
Parent(index) = floor(index/2)
2. The height of a complete binary tree with n nodes is the tight bound of log n (which is why the operations for a max-priority queue have logn worst-case running time)
**Max-Heap property**: Every node has a key (priority) greater than or equal to the keys of its immediate children, implying that every node is larger than or equal to all of its descendants (i.e. every subtree of a heap is also a heap).
Now that we have defined a few things, we can work on the operations!
**Max(Q): Returns the largest key in Q in O(1) time**
Because of the max-heap property, we just have to return Q[1]! The worst case is then the tight bound of 1.
**Insert(Q, x): Insert node x into heap Q in O(log n) time**
First thing to note: Which spot do we add the new node? We would need to add x to the end of the heap to keep it a complete binary tree. However, the heap property might be broken. X could be greater than its parent node. If that's true, we should 'bubble-up' the new node to a proper position by swapping with the parent and keep doing this until it is less than its parent. This operation's worst case is then O(height) = O(log n).
**ExtractMax(Q): Delete and returns the largest key in Q in O(logn) time**
How do we delete the root and keep the heap a complete binary tree? The only spot we can delete to keep a complete binary tree is the last element, but we want the root to be deleted! Our solution is to overwrite the root with the last key and then delete the last guy. Now that the max-heap property is broken, we need to fix it by swapping (or 'bubbling down') with a child.. but which child do we swap with? We swap with the elder child because it's the largest among the three and we want to maintain the max-heap property.

----------

Lecture 3: Binary Search Trees, BST sort



<h1 id="stacks-queues-heaps">Stacks, Queues, and Heaps</h1>

<h1 id="bsts">Binary Search Trees</h1>

<h1 id="hashing">hashing</h1>

<h1 id="sorting">Sorting Algorithms</h1>
<h2 id="insertion-sort">Insertion Sort</h2>
<h2 id="merge-sort">Merge Sort</h2>
<h2 id="quick-sort">Quick Sort</h2>
<h2 id="heap-sort">Heap Sort</h2>

<h1 id="#graphs">Graphs</h1>
<h2 id="bfs">Breadth First Search</h2>
<h2 id="dfs">Depth First Search</h2>
<h2 id="minspantrees">Minimum Spanning Trees</h2>

<h1 id="#disjoint-sets">Disjoint Sets</h1>

<h1 id="#shortest-paths">Shortest Paths</h1>
<h2 id="#dijkstra">Dijkstra</h2>
<h2 id="#bell-ford">Bellman-Ford</h2>
<h2 id="#extra-paths">Extras</h2>
</article>
</body>
</html>
