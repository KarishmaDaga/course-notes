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
# CISC 223: Software Specifications

## Topics

* [Alphabets, Strings, and Languages](#alph-str-lang)
  * [Halting Problem](#halting)
  * [Classification of Computing Problems](#classification)
  * [Modelling Decision Problems](#modelling)
  * [Inductive Definition of Sets and Structural Induction](#induction)
* [State-Transition Diagrams](#alph-str-lang)
* [Regular Expressions vs State Diagrams](#reg-exp)
* [Minimizing State Transition Diagrams, Nonregular Languages](#min-state-trans-diagrams)
* [Context-free Languages](#context-free-lang)
* [Parsing](#parsing)
* [Specifying Algorithms](#specifying-alg)
* [Verifying Algorithms](#verifying-alg)
* [Additional Verification Techniques](#more-verification)
* [Unimplementable Specifications](#more-verification)
* [Loop Invariants and other topics](#loop-invariants)

<hr>
<h1 id="#alph-str-lang">Alphabets, Strings, and Languages</h1>

#### What do computers do?
They solve **decision problems**.
Decision Problems involve taking an **input** and producing a binary **output**.

An **input**, abstractly, is a finite string on a finite alphabet (set of characters).

**Algorithms**: a finite time for processing

An **output** is either true or false.

#### Other important questions:
* #### What are computers?
* #### Which tasks can a computer carry out?
* #### Which tasks are easy/hard for computers?

**Formal Methods**: the application of logic, formal languages, automata theory, and more problems in software and hardware specification and verification.

The uses of formal methods:
* lexical and parsing stages of compiler construction
* use of regular expressions in text editors
* state-charts in object oriented modelling
* circuit design
* DNA and protein sequence matching (! what)

It also acts as an 'early warning system' for what is programmatically impossible.
There exist more computing problems than the number of all possible programs, so there exist problems that are not solvable by an program or algorithm (even if it is given unbounded space and time to perform its operations).

<h2 id="halting">**Famous example: The Halting Problem**</h2>

[Good Reference for this topic](http://www.cgl.uwaterloo.ca/csk/halt/)

Alan Turing proved an analagous theorem in CS to Kurt Gödel's. He showed that there must exist undecidable problems (a program is decidable if it has a solution. It is undecidable if it does not in a finite time). The proof works by defining a problem (the halting problem) and proving that it can't be solved.

So, given a program *P* and an input *x* to the program, will *P* ever stop running when given *x* as an input?

Proof: Suppose (to the contrary) that *T* is a program that solves the halting problem. We'll use T as a black box (halting problem solver) to come up with a new program called *meta T*.

```
def metaT(P):
  run T on (P,P):
  if T says that P halts:
    loop infinitely
  else:
    halt and output "success"
```
MetaT accepts as input the source code of the program P and then uses T to tell if P halts (when given its own source code as input).
So, metaT behaves the opposite of P. If P halts then metaT loops infinitely and if P doesn't terminate, then metaT terminates as well.

#### What happens if we run metaT on itself?
```
metaT(metaT)
```
* Assume metaT's output is "Yes, it does halt"
* metaT then loops infinitely
* Then metaT, the program, proceeds to loop forever
* contradiction!
* metaT(metaT) doesn't halt, contradicting T's answer. So T cannot be correct, and the halting problem cannot be solved.

<h3 id="classification">Classification of Computing Problems</h3>
1. Uncomputable: even in principle cannot be solved by an algorithm
2. Solvable using unlimited resources (of time and space) but not with limited resources
3. Solvable with limited resources

Simple Problem: Test whether an arbitrary input strings (sequences of symbols/characters) can be matched given a pattern?

Efficient Techniques:
* State-transition diagrams (automata): simple simulated machines
* Regular Expressions: rules for building patterns
* Grammars: rules for generating patterns

<h2 id="modelling">Modelling Decision Problems: Alphabets, Strings, languages</h2>

We model decision problems using *formal languages*.

A decision problem has two components:
* A domain set X
* a language L that is a subset of X (L <= X)

Our decision problem is then *"for some x which is an element of X, is x an element of L"*? Example:
* x is an element of the set of all integers Z and L = set of prime numbers
* x = set of all email messages and L = set of all spam emails
* x = set of graphs and L = set of connected graphs

#### alphabet: denoted ∑, finite non-empty set of elements. Elements are called symbols or characters.
Example: ∑ = {a, b}, ∑ = {0, 1}, ∑ = {0, 1, 2, 3}.

#### String: denoted ∑* represents the set of all _finite_ strings over the alphabet ∑. Note: ∑* is an infinite set, but its members are finite.

**empty string**: denoted 𝜀. 𝜀 is a string over any alphabet.
**length**: (of a string) number of occurrences of symbols in it.

#### Languages: subsets of ∑* (Language: collection of strings)
Example:
* L = empty set --> empty language (magnitude of L = 0)
* L = {𝜀} Non-empty language that contains one element.
* L = {𝜀, 0, 01, 0111}
* L = {∑* }

A compiler's task of checking their input (the code of a program) to see if the program is valid (if the code is in the language), can be seen as checking **membership** in such a language.

<h2 id="induction">Inductive Definition of Sets and Structural Induction</h2>

### Formal tools for Defining Sets
We want languages to be able to model every computational task. We need several different methods formally defining sets since all languages are sets.

1. List all members of a set: precise and concrete, but it makes lookups difficult (O(n)) and it fails if the set is infinitely large.
2. Set builder notation: defining sets that are infinite based on common properties that all members share
3. Inductive Definitions: Requires three components:
  * A domain set X
  * A core set A (i.e. atoms) (ex: {me})
  * a set of operations P

  Example: Set of all blood relatives. A = {me}, X = {set of all blood relatives}, and P = {"son of", "mother of", ...}. The set P is a set of functions mapping from X -> X.

  Given these components, we can define the inductive set I(A, P) as all domain elements that can be reached from the core set by applying a finite sequence of operations from P.

  #### Inductive Set: defined by core set A and operations P - is the _smallest set_ satisfying:
  * contains all members of A
  * closed under operation in P

  

<h1 id="#state-transition">State-Transition Diagrams</h1>

<h1 id="#reg-exp">Regular Expressions vs State Diagrams</h1>

<h1 id="#min-state-trans-diagrams">Minimizing State Transition Diagrams, Nonregular Languages</h1>

<h1 id="#context-free-lang">Context-free Languages</h1>
<h1 id="#parsing">Parsing</h1>
<h1 id="#specifying-alg">Specifying Algorithms</h1>
<h1 id="#verifying-alg">Verifying Algorithms</h1>
<h1 id="#more-verification">Additional Verification Techniques</h1>
<h1 id="#unimplementable">Unimplementable Specifications</h1>
<h1 id="#loop-invariants">Loop Invariants and other topics</h1>
