<style>
h1 a {
  display: none;
}

.container-lg {
  min-width: 200px;
  max-width: 880px;
  padding: 45px;
}

</style>

[All Notes](http://karishmadaga.com/course-notes) // [About](http://karishmadaga.com)
# CISC 260: Programming Paradigms

* [Course reference, Stanford](http://www.scs.stanford.edu/14sp-cs240h/).
* [Course reference, UofT 💖](http://www.cs.toronto.edu/~david/courses/csc324_w15/).
* [Course Notes, UofT](http://www.cs.toronto.edu/~david/courses/csc324_w15/res/notes.pdf)

### Administrative Details:
* Office Hours: Goodwin 527 from 1-2 pm on M/T/Th (may change).
* There are assigned readings, so do them!
* 6 assignments worth **10%**
* 3 tests worth **50%** (dates are up!)
* final exam **40%**
* [Haskell Textbook](https://www.dropbox.com/s/gqjy014sczztzs6/Haskell%2C%20The%20Craft%20of%20Functional%20Programming%20-%20Simon%20Thompson.pdf?dl=0)
* [Prolog Textbook](https://www.dropbox.com/s/h54llblznzs8v4d/Prolog%20Programming%20for%20Artificial%20Intelligence%20-%20Ivan%20Bratko.pdf?dl=0)


## Topics

* [Course Overview](#overview)
* [Lambda Calculus](#lambda)
  * [Alonzo Church](#history)
* [Intro to Haskell](#intro-haskell)
  * [Recursion](#recursion)
  * [Lists and Tuples](#list-tuple)
  * [Proofs](#proofs)
  * [High Order Functions](#high-fnc)
  * [Types and Type Checking](#types)
  * [Algebraic Types](#alg-types)
  * [Lazy Programming](#lazy)
* [Intro to Prolog](#prolog)
  * [Prolog Lists and Arithmetic](#list-arith)
  * [Cuts and Negotiation](#cuts)
  * [Searching](#searching)


## Assigned Readings
* Week 1: Chapters 1-3 of Haskell TB.

<hr>

<h1 id="overview">Course Overview</h1>

#### Jan 8, 2018
## Programming Paradigms
* a framework for thinking about programming
* a pattern or model for how we program
* just like software engineering is defined by different methodologies, programming languages are defined by differing _paradigms_
* some languages are designed to support one paradigm (ex: Haskell supports functional programming) while other programming languages support multiple paradigms (ex: Java, C++, Scala, Python, Scheme, etc)

### Types of Paradigms
1. Procedural/Imperative: giving commands to the computer
  * e.g.: accessing and modifying memory
  * languages: assembly, C, fortran, Pascal
2. Object oriented: describe data structures and what you can do with them
  * e.g.: C++, Java, Kotlin, etc.
  * note: the methods are still imperative!
3. Event-driven: describes how to react to events
  * e.g.: JavaFX
4. Functional: describes the desired result in mathematical forms
  * programs are treated as a sequence of stateless function evaluations
  * e.g.: Haskell, Lisp, ML, Rust 💖
5. Logical: describes logical properties, relationships between values
  * e.g.: Prolog
6. Others: event simulation, tree transformation, etc.

### Applications of Haskell
* financial analysis (OCaml @Jane Street)
* modelling (biochemistry)
* internal tools @facebook
* managing clusters of servers @google

### Applications of Prolog:
* environmental systems (weather predictions)
* Boeing corp, electrical assembly tasks
* geology: finding gold
* rapid prototyping of AI problems

<h1 id="lambda">Lambda Calculus: A prelude</h1>

In the 1930s, in the process of trying to solve a mathematical logic problem, Turing developed an abstract model of mechanical, procedural computation: a machine that could read in a string o 0's and 1's, a finite state control that could make decisions and write 0's and 1's to its internal memory, and an output space where the computation's result would be displayed. The fundamental mechanism of the Turing machine - reading data, executing a sequence of instructions to modify internal memory, and producing output - would soon become the von Neumann architecture lying at the heart of modern computers.

<h2 id="history">Alonzo Church</h2>

Shortly before Turing published his paper introducing the Turing machine, the logician Alonzo Church had published a paper resolving the same fundamental problem using entirely different means. Church drew inspiration from the mathematical notion of _functions_ to model computation. These both radically different notions of computation were in fact _equivalent_. They went a step further in the **Church-Turing Thesis** to say that _any_ reasonable computational model could be just as powerful as their two models (and it still holds today!). Yet, Turing's ideas are at the base of many core cs applications (hardware, programming languages, etc). What were Church's ideas?

### Lambda Calculus
Church modelled computation with **lambda calculus**, which was heavily influenced by the mathematical notion of a function. This model has just 3 ingredients:

1. Names: _a, x, hello,_ etc. These are just symbols w/ no meaning
2. Function Creation: λx→x. This expression creates a function that simply returns its argument - the identity function.
3. Function application: _f x_. This expression applies the function _f_ to the value _x_.

#### Lambda calculus views _functions_ as the primary ingredient of computation; functions can be created and applied to values, which are themselves functions, and so through combining functions we may create complex computations.

There is no concept of _time_ required for a certain sequence of 'steps', and there is no external or global _state_ which can influence their behaviour.

### A Paradigm Shift (In You)
The influence of Church's lambda calculus is most obvious today in the _functional programming paradigm_, and it had heavily influenced languages like Lisp, ML, Haskell (which we will be learning in this course), and more. The goal of this course is to open our minds to different ways of solving problems and to approach problems more algorithmically.

<h1 id="intro-haskell">Intro to Haskell</h1>

<h1 id="prolog">Intro to Prolog</h1>
