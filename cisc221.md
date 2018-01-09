
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
# CISC 221: Computer Architecture


## Topics

* [Character Encodings](#Character-Encodings)
  * [Abstraction](#Abstraction)
  * [Endianness](#Endianness)
  * [ASCII](#ASCII)
  * [Unicode](#Unicode)
  * [Hexadecimal](#Hexadecimal)
* [Machine-Level Representation of Programs](#machine-level-rep)
  * [Machine Architecture - ARM, IA-32, etc](#machine-arch)
  * [Assembly Language Programming](#assembly)
* [Digital Logic](#digital-logic)
* [Enhancing Performance](#enh-perf)
  * [Pipelining and Caching](#pipelining)
  * [Instruction-level parallelism](#parallelism)
  * [Superscalar processors, multiprocessors, and clusters](#processors)
* [The Memory Hierarchy](#memory-hierarchy)
* [Exceptions, Devices, Interrupts](#excep-dev-interr)
  * [I/O, Role of Operating Systems, Interrupts and Traps](#i-o)
  * [Interrupt service routines, event driven programming](#event-driven-pro)

## Extra Reading
* [Machine-Level Representation of Programs, CMU](http://csapp.cs.cmu.edu/2e/ch3-preview.pdf)
* [Hexes and other Magical Numbers - Vaidehi Joshi](https://medium.com/basecs/hexs-and-other-magical-numbers-9785bc26b7ee)
* [Bits, Bytes, Building with Binary - Vaidehi Joshi](https://medium.com/basecs/bits-bytes-building-with-binary-13cb4289aafa)
* [A Most Perfect Union: Just-In-Time Compilers - Vaidehi Joshi](https://medium.com/basecs/a-most-perfect-union-just-in-time-compilers-2938712a9f6a)
<hr>
<h1 id="#data-rep">Data Representation</h1>

## Abstraction
Abstraction is the process of removing or hiding irrelevant details.  Everything is just a sequence of bits (binary digits).  There are two possible values for a bit, and those values can have arbitrary labels such as up/down, left/right, 0/1, on/off, pass/fail.
Since there can be k places and 2 choices for each, there are 2^k combinations.

## Endianness
Consider the sequence 1010. This sequence of bits has different interpretations when following different conventions.

* Unsigned, little-endian: (1 x 2^0) + (0 x 2^1) + (1 x 2^2) + (0 x 2^3) = 1 + 4 = 5
* Unsigned, big-endian: (0 x 2^0) + (1 x 2^1) + (0 x 2^2) + (1 x 2^3) = 10
* Two's complement, little-endian
* 


<h1 id="#machine-level-rep">Machine-Level Representation of Programs</h1>

<h2 id="#machine-arch">Machine Architecture - ARM, IA-32, etc</h2>

<h2 id="#assembly">Assembly Language Programming</h2>

<h1 id="#digital-logic">Digital Logic</h1>
<h1 id="#enh-perf">Enhancing Performance</h1>
<h2 id="#pipelining">Pipelining and Caching</h2>
<h2 id="#parallelism">Instruction-level Parallelism</h2>
<h2 id="#processors">Superscalar Processors, Multiprocessors, and Clusters</h2>

<h1 id="#memory-hierarchy">The Memory Hierarchy</h1>
<h1 id="#excep-dev-interr">Exceptions, Devices, Interrupts</h1>
<h2 id="#event-driven-pro">Interrupt service routines, event driven programming.</h2>
