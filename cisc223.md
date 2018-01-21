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
# CISC 223: Introduction to the Theory of Computation

## Topics

* [Halting Problem](#halting)
* [Classification of Computing Problems](#classification)
* [Modelling Decision Problems: Alphabets, Strings, and Languages](#modelling)
* [Inductive Definition of Sets and Structural Induction](#induction)
* [Regular Expressions and their Operations](#Regular-Expressions-and-their-Operations)
* [Finite Automata](#finite)
  * [DFAs and NFAs](#determinism)
* [Regular Expressions vs State Diagrams](#reg-exp)
* [Minimizing State Transition Diagrams, Nonregular Languages](#min-state-trans-diagrams)
* [Context-free Languages](#context-free-lang)
* [Parsing](#parsing)
* [Specifying Algorithms](#specifying-alg)
* [Verifying Algorithms](#verifying-alg)
* [Additional Verification Techniques](#more-verification)
* [Unimplementable Specifications](#more-verification)
* [Loop Invariants and other topics](#loop-invariants)

## Extra Reading and Textbook Resources

* [Introduction to the Theory of Computation, aka BAE TB 💖](http://fuuu.be/polytech/INFOF408/Introduction-To-The-Theory-Of-Computation-Michael-Sipser.pdf)
* [MIT OCW lecture notes](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-045j-automata-computability-and-complexity-spring-2011/lecture-notes/)
* [Inspo to Keep Studying: Real Life Applications](https://luckytoilet.wordpress.com/2018/01/01/real-world-applications-of-automaton-theory/)
<hr>

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

<h2 id="halting">Famous example: The Halting Problem</h2>

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
* a language L that is a subset of X (L ⊆ X)

Our decision problem is then *"for some x which ∈ of X, is x an element of L"*? Example:
* x ∈ of the set of all integers Z and L = set of prime numbers
* x = set of all email messages and L = set of all spam emails
* x = set of graphs and L = set of connected graphs

#### Alphabet: denoted ∑, finite non-empty set of elements. Elements are called symbols or characters.
Example: ∑ = {a, b}, ∑ = {0, 1}, ∑ = {0, 1, 2, 3}.

#### String: denoted ∑* represents the set of all _finite_ strings over the alphabet ∑. Note: ∑* is an infinite set, but its members are finite.

**Empty String**: denoted ε. ε is a string over any alphabet.
**length**: (of a string) number of occurrences of symbols in it.

#### Languages: subsets of ∑* (Language: collection of strings)
Example:
* L = empty set --> empty language (magnitude of L = 0)
* L = {ε} Non-empty language that contains one element.
* L = {ε, 0, 01, 0111}
* L = {∑* }

A compiler's task of checking their input (the code of a program) to see if the program is valid (if the code is in the language), can be seen as checking **membership** in such a language.

#### Quick Summary Example:
* ∑ = {a, b, ...}
* ∑* = {ab, abb, bab, ...}
* L = {ab, bab, baa} where L⊆∑*


### More Terminology:
* prefix: any initial part of the string (must include the first symbols)
* suffix: any end part of the string (must include the last symbols)
* substring: any range of symbols of the string

Example: ∑ = {a, b, c} and S = abac
prefixes: ε, a, ab, aba, abac
suffixes: c, ac, bac, abac
substrings: all of the prefixes, suffixes, and _ba_ and _b_


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

*Given a set (language) defined inductively, how can we tell if some x∈X is in the language (x∈L) or not (x∉L)?*
* Proving membership is a lot easier than proving non-membership.

![alt text](structural-induction-example2.png)

*We need to generate abbaa from the core set and its operations.*


1. a belongs to the core set A
2. we get 'baa' after applying P_3(a,a)
3. 'abbaa' after applying P_4(a, baa)

*Is ε ∈ I(A, P)?*
- NO.
  - Each operation in P increases length (simple reasoning)
  - This is more difficult than proving membership

#### Closure: A set B is closed under the operations of P if for every f∈P and every x,y∈B, f(x,y)∈B.

**So the inductive set can _also_ be defined as the intersection over the _entire_ collection of sets that satisfy closure**

<h2 id="Regular-Expressions-and-their-Operations">Regular Expressions and their Operations.</h2>

Recall: Tasks will always be a decision problem. A decision problem is *"for some x ∈ X, is x an element of L"*? The set of all possible tasks is {L : L ⊆ {a,b}* }. This set is an infinite set of finite strings.

#### Regular Language: A language L is _regular_ if L can be built from the symbols of Σ and Ø using the operations union, concatenation, and kleene star (closure). A representation of L in this form is called a regular expression for L.
* Note (test trick question): {ε} is regular because {ε} = Ø*

### Operations on Languages:

* **Concatenation (•)**: Suppose there are two regular languages R and S that are the subset of Σ*, we can define the concatenation of them RS = {rs: r∈R, s∈S}.
  * Example: Let R = {0, 011} and S = {ε, 110}. Then RS = {0, 0110, 011, 011110}.
  * Note! Concatenation is not always **commmutative** (xy != yx), but it is **associative** ( x(yz) = z(yx) ).
* **Union (∪)**: Suppose there are two regular languages R and S that are the subset of Σ*, we can define the union of them R + S = { w∈Σ* : w∈R or w∈S}.
  * Example: Let R = {a, ab} and S = {bc, c}. R + S = {a, ab, bc, c}.
* **Kleene Star / Closure (raised * )**: Suppose there is a regular language R that is a subset of Σ*, we can define the kleene star of R as R* = {r1r2 • ... •rn : ri ∈ R where i∈N and where n >= 0}. It is essentially the concatenation of the set R with itself _i_ times. R_i is the set of all strings that can be represented as the concatenation of _i_ strings in R.
  * Example: {"ab","c"}* = {ε, "ab", "c", "abab", "abc", "cab", "cc", "ababab", "ababc", "abcab", "abcc", "cabab", "cabc", "ccab", "ccc", ...}.
  * Example: Ø* = {ε}.

#### Examples of Regular Language Operations where Σ = {a, b}:
* all strings that have suffix babbb
  * (a + b)* babbb
* all strings that have substring bbbb
  * (a + b)* bbbb (a + b)*
* all strings where the first and last symbols are different
  * a(a+b)* b + b(a + b)* a

<h1 id="finite">Finite Automata</h1>

* computational model: idealized models of computers that we use to build a manageable mathematical theory of them directly
* the simplest model is called the **finite state machine or finite automata**.
* finite automata are good models for computers with an extremely limited amount of memory

Example: the controller for an automatic door. The controller is in either of two states: "OPEN" or "CLOSED", representing the corresponding condition of the door. There are four possible input conditions:
  * "FRONT" (person is standing in front of the door)
  * "REAR" (person is standing to the rear of the door)
  * "BOTH" (people are standing both in front and rear to the doors)
  * "NEITHER"(no one is standing in front or at the rear of the door)
    ![finte-automata-example](finite-automata-example.jpeg)


State (Open, Closed) x Input Signal (Front, Rear, etc)

 State | NEITHER | FRONT | REAR | BOTH  
--- | --- | --- | --- |
OPEN | CLOSED | OPEN | CLOSED | CLOSED
CLOSED | CLOSED | OPEN | OPEN | OPEN

The controller moves from state to state, depending on the input it receives.

## Formal Definition of Finite Automata

* A finite automaton is 5-tuple (a list of 5 elements) which consists of states and rules for an FA.

#### A finite automaton is a 5-tuple (Q, Σ, δ, q_o, F) where:
1. Q is a finite set called the _states_
2. Σ is a finite set called the _alphabet_
3. δ: Q x Σ --> Q is the _transition function_, which defines the rules for moving.
4. q_o ∈ Q is the _start state_
5. F ⊆ Q is the _set of accept states_

We can then use the formal definition of FAs to define the following example:
![finite example](fa-ex1.jpeg)

We can then say that A is the set of all strings that machine M accepts and that A is the language of the machine, L(M) = A. A language is called a **regular language** if some finite automaton recognizes/accepts it.

<h2 id="determinism">Nondeterminism</h2>

#### Deterministic: when the machine is in a given state and reads the next input symbol, we know what the next state will be
#### Nondeterministic: several choices may exist for the next state at any point

Nondeterminism is a generalization of determinism, so every DFA is automatically an NFA.

Differences between DFAs and NFAs:
* Every state of a DFA always has exactly one transition arrow for each symbol in the alphabet. In an NFA, a state may have zero, one, or many exiting arrows for each alphabet symbol.
* In a DFA, inputs are elements from the alphabet. NFA may have inputs that are elements from the alphabet _and_ . Zero, one, or many arrows may exit from each  state with the label .

#### So how does an NFA compute?
An NFA kinda works like a parallel computation, where there are multiple independent processes that run concurrently. Suppose we're running an NFA on an input string and we come to a state with multiple ways to proceed. The machine splits into multiple copies of itself and follows _all_ the possibilities in parallel. Each copy of the machine takes one of the possible ways to proceed and continues as before. If there are subsequent choices, the machine splits again. If the next input symbol doesn't appear on any of the arrows exiting the state occupied by a copy of the machine, the copy of the machine dies, along with the branch of the computation associated with it. Finally, if _any one_ of these copies of the machine is in an accept state at the end of the input, the NFA accepts the input string. If ε is on an arrow, without reading the input, the machine splits into multiple copies and proceeds nondeterministically as before.

You can also think of nondeterminism as a tree of possibilities.

### Formal Definition of a NFA
Similar to that of a DFA, except for the transition function. In a NFA, the transition function takes a state and an input symbol _or the empty string_ and produces _the set of possible next states_. For any set Q we write P(Q) to be the collection of all subsets of Q. Here, P(Q) is the **power set** of Q. We also define for any alphabet Σ, **Σ_ε = ΣU{ε}**.

**A nondeterministic finite automaton is a five tuple (Q, Σ, δ, q_o, F) where:**
1. Q is a finite set called the _states_
2. Σ is a finite set called the _alphabet_
3. δ: Q x Σ_ε --> P(Q) is the _transition function_, which defines the rules for moving.
4. q_o ∈ Q is the _start state_
5. F ⊆ Q is the _set of accept states_


Example NFA:
![nfa-example](nfa-example-1.jpeg)

## TODO: Converting a NFA to a DFA
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
