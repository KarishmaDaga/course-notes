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
* [Course reference, UofT](http://www.cs.toronto.edu/~david/courses/csc324_w15/).
* [Course Notes, UofT](http://www.cs.toronto.edu/~david/courses/csc324_w15/res/notes.pdf)

### Administrative Details:
* Office Hours: Goodwin 527 from 1-2 pm on M/T/Th (may change).
* There are assigned readings, so do them!
* 6 assignments worth **10%**
* 3 tests worth **50%** (dates are up!)
* final exam **40%**


## Topics

* [Course Overview](#overview)
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

<h1 id="intro-haskell">Intro to Haskell</h1>

<h1 id="prolog">Intro to Prolog</h1>
