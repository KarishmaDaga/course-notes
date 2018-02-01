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
* [Haskell Full Tutorial](http://learnyouahaskell.com/introduction#about-this-tutorial)

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
  * [A Paradigm Shift (In You)](#a-paradigm-shift-in-you)
* [Intro to Haskell](#Intro-to-Haskell)
  * [Online Tutorial Notes](#Online-Tutorial-Notes)
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
* Week 2: [Chapter 4](chapter-4-260-readings.md)

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

In the 1930s, in the process of trying to solve a mathematical logic problem, Turing developed an abstract model of mechanical, procedural computation: a machine that could read in a string of 0's and 1's, a finite state control that could make decisions and write 0's and 1's to its internal memory, and an output space where the computation's result would be displayed. The fundamental mechanism of the Turing machine - reading data, executing a sequence of instructions to modify internal memory, and producing output - would soon become the von Neumann architecture lying at the heart of modern computers.

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

# Intro to Haskell

#### Jan 9 2018, required reading: chapters 1-3 of Haskell Textbook (not very long)
* Ch 1: Overview
* Ch 2: using Hugs/GHC, simple definitions
* Ch 3: basic haskell types, conditionals, some other important rules

Haskell is a large language. At its core, it is functional. On the outside, it has a specialized layer consisting of I/O, monads, etc. We're not allowed to use those for tests and projects.

```
Prelude> 7 + 2
9
Prelude> 3*(2+4)
18
-- floating point division, full value.
Prelude> 14.0/3.0
4.667
Prelude> 14 / 3
4.667
-- integer division, truncated. div is a function for this.
-- Recall: functions in haskell are as f x
Prelude> div 14 3
4
Prelude> mod 14 3
2
Prelude> sqrt 35
5.916..
-- it means the value of the last expression we computed, only works interactively
Prelude> it + 5
10.916..
```

First script example, very primitive haskell program
```
module Jan09 where
a = 43
b = a + 1
year = 2018

plus1 x = x + 1

average x y = (x + y) / 2

intAvg x y = div (x + y) 2

a :: integer
-- cannot use operations like sqrt that need a floating point number

-- list of type of chars
"abc" :: [Char]
```
We can load this into a compiler or run it from the terminal.

lost track around 11 pm, watch lecture video from that point...
covered functions, conditionals, and variables

# Online Tutorial Notes

In imperative languages such that Java, we can give computers a sequence of tasks and then it executes them. While executing them, it can change state:

```
a = 5

// sometime later

a = "dog"
```

You also have control flow structures for doing some action several times.

#### In purely functional programming, you don't tell the computer what to do as such, but rather you **tell it what stuff _is_**.
* The factorial of a number is the product of all the numbers from 1 to that number
* the sum of a list of numbers is the first number plus the sum of all the other numbers, and so on.

You express the above in the form of _functions_.
You also can't change the state of a variable.

#### Haskell is _lazy_.
* haskell won't execute functions and calculate things until it's really forced to show you a result
* that allows you to think of programs as a series of **transformations on data**. It also allows cool things such as ~infinite data structures~ (quoi?!)
* haskell is **statically typed**. When you compile your program, the compiler knows which piece of code is a number, which is a string, and so on, so a lot of errors are caught at compile time rather than runtime.
  * if you try to add a number and a string, haskell will whine at you (it has a v. good type system that has **type inference**, so you don't have to explicitly label every piece of code with a type)
* haskell is **elegant and concise**

### Simple Examples

```
Prelude> 2 + 15
17
Prelude> 49 * 100
4900
Prelude> 1892 - 1472
420 :')
Prelude> 5 / 2
2.5
Prelude> div 5 2
2
Prelude> True && False
False
Prelude> False || True
True
Prelude> 5 == 5
True
Prelude> not False
True
Prelude> "hello" == "hello"
True
Prelude> succ 8
9
Prelude> min 9 10
9
Prelude> max 3.4 5
5
Prelude> succ 9 + max 5 4 + 1
16
```

### Week 2: See readings [here](chapter-4-260-readings.md)

#### Week 2 Lecture 1, Jan 15 2018
??? See lecture slides I guess and add em here

#### Week 2 Lecture 2, Jan 16 2018

##### Numerical Examples:
* factorial
* ask if integer is power of 2
* sumfunc f x y = f(x) + f(x+1) + ... + f(y)
* ask if an integer is prime
  * How do we know if something is prime? A number is prime if it cannot be written as the product of values other than itself and 1.
  * Sieve of Eratosthenes
* Count number of primes <= N
* Find the first prime >= N
* Find the smallest factor of an integer

Note: Higher order function: function that produces other function(s)

```
-- review type declarations in function definitions
sumfunc :: (Integer -> Integer) -> Integer -> Integer -> Integer
sumfunc f low high
  | low > high = error "lower value is greater than high"
  | low == high = f low
  | otherwise = (f low) + sumfunc f (low + 1) high

-- define function here for f in sumfunc
testFunc x y = x*2
```

```
isPrime :: Int -> Bool
isPrime n = not (hasFactors n 2 (n-1))

hasFactors :: Int -> Int -> Int -> Bool
hasFactors n low high
  | mod n low == 0 = True
  | otherwise = hasFactors n (low + 1) high

-- Looking ahead
filter isPrime [2...50]
-- returns list of prime numbers from 2-50
```

```
countPrimesLeq :: Integer -> Integer
countPrimesLeq n
  | n < 2 = 0
  | isPrime n = countPrimesLeq (n - 1) +1
  | otherwise = countPrimesLeq (n - 1)
```

```
firstPrimeGeq n
  | isPrime n = n
  | otherwise = firstPrimeGeq (n + 1)
```

```
-- Find smallest factor of an integer (not including 1)
smallestFactor n = smallestFactorGeq n 2

smallestFactorGeq n start
  | mod n start == 0 = start
  | otherwise = smallestFactorGeq n (start + 1)
```

#### Week 2 Lecture 3 Missing -> Do Lecture notes on video

#### Week 3 Lecture 1 Jan 22, 2018
Example of a higher-order function:
```
-- @params: f is a function, low is a lower bound, and
-- high is an upper bound

square n = n*n
sumFunc1 f low high
  | low > high = 0
  | otherwise = f low + sumFunc1 f (low + 1) high
```
Types of recursion (read up on these different types and do practice problems):
- simple recursion
- tail recursion
- multiple recursion

```
sumFunc2 f low high ...
```

```
sumFunc3 f low high
  | low > high = 0
  | low == high = f low
  | otherwise = sumFunc3 f low mid + sumFunc3 f (mid + 1) high
  where
  mid = div (low + high)
```

Question: What does this function do?
```
puzzle :: Int -> Int -> Int
puzzle x n
  | n == 0 = 1
  | n == 1 = x*n
  | x < 2 = x*n       -- case for when n == 2
  | n > x = (puzzle (2*x) (n-x)) + 7
  | otherwise = 3 * (puzzle (n+x) (n-1))
```
What kind of recursion is this, and what is the value of ```puzzle 2 5```?
- n > x since 5 > 2, so:
  - ```puzzle (4) (3)  + 7```
  - 3 is not greater than 4, so ```[3 * puzzle (7) (2)] + 7```
    - ```(3 * (3 * puzzle (9) (1))) + 7```
    - ```(9 * puzzle (9) (1)) + 7```
      - ...


What kind of recursion is this, and what is the value of ```challenge 2 4```?

```
challenge :: Int -> Int -> Int
challenge x n
  | n == 0 = 1
  | n == 1 = x
  | x < 2 = x*n
  | n > x = challenge (2*x) (n-x) + challenge (x + 1) (n - x)
  | otherwise = challenge (n + x) (n - 1) + challenge (x + 1) (n - 1)
```
- ```challenge 2 4``` and 4 > 2, so:
  - ```challenge (2*2) (4-2) + challenge (2+1) (4-2)```
  - ```challenge (4) (2) + challenge (3) (2)```
    - ```challenge (4) (2)```
      - ```challenge (4 + 2) (2 - 1) + challenge (4 + 1) (2 - 1)```
      - ```challenge (6) (1) + challenge (5) (1)```
        - ```challenge (6) (1)``` = 6*1 = 6
        - ```challenge (5) (1)``` = 5*1 = 5
  - ```challenge (3) (2)```:
    - ```challenge (5) (1)
```

## Lists

#### Week 3 Lecture 2 Jan 23, 2018
##### Reading: [Chapters 5 and 7](260-ch5-7.md), skip parts referring to algebraic types.

- homogeneous data structure (everything contained in a list is of the same type)
- lists are immutable (all values in functional Haskell are immutable)
- lists of same type may vary in size
- compare to python lists or java arraylist

### Naming Types
- Use type keyword to give "nicknames" to types.
  - type ID = Int
  - type Height = Float
  - type Vector = (int, int)
  - type String = [Char]. Strings are lists of characters.

### Recursive View of Lists
- a list has one of two forms:
  - the special value [] (empty)
  - A list element (the _head_) and a list containing the remaining elements (the _tail_)
    - Example: A list of integers: ```[42, 37, 15, 8]``` can also be expressed as:
      - head: ```42```, and the
      - tail: ```[37, 15, 8]```
- Lists are not arrays! think of them as linked lists

### Basic List Operations
- Some functions to extract parts of lists:
  - ```head```: Takes a list and returns its head (first element).
    - ```head [1, 2, 3] = 1```
  - ```tail```: Takes a list and returns its tail (chops off first element)
    - ```tail [1, 2, 3] = [2, 3]```
  - ```last```: takes a list and returns its last element
  - ```init```: takes a list and returns everything except its last element
  - ```length```: gets length of list
  - ```null```: checks if a list is empty. If it is, it returns ```True```, otherwise it returns ```False```.
  - ```reverse```: reverses a list
  - ```take```: takes a number n and a list. It extracts n elements from the beginning of the list.
  - ```drop```: works in a similar way, but it removes the first n elements and returns the new list.
  - ```minimum```: returns smallest in list
  - ```maximum```: returns largest in list
  - ```sum```: takes a list of numbers and returns their sum
  - ```product```: takes a list of numbers and returns their product
  - ```elem```: takes a number and a list and tells us if the num is an element of the list.
    - ``` 4 `elem` [2, 3, 4, 6]```
  - ```cycle```: takes a list and cycles it into an infinite list. This will go on forever, so you should slice it off somewhere using ```take```.
- Operator ```:``` constructs a list from a head and tail. Pronounced "cons" for _construct_. This is great for concatenating large lists.
  - ```1 : [2, 3]``` is equal to ```[1, 2, 3]```
  - ```'A':" SMALL CAT"``` yields ```"A SMALL CAT"```
- Texas Ranges: shortcuts for lists of numbers:
  - ```[2..7] =[2,3,4,5,6,7]```
  - ```[3,5..17] = [3,5,7,9,11,13,15,17]```
  - ```[7,6..1] = [7,6,5,4,3,2,1]```
  - ```[5..2] = []```
  - ```[5,6..4] = []```
- Concatenating Lists:
  - ```[1, 2, 3, 4] ++ [9, 10, 11, 12]``` yields ```[1, 2, 3, 4, 9, 10, 11, 12]```
  - ```"hello" ++ " " ++ "world"``` yields ```"hello world"```
  - The ```++``` operator is fine to use on small lists, but concatenating very large lists will take a long time since Haskell has to walk through the whole list on the left side of ```++```
- Getting an element out of a list by index, ```!!```:
  - ```"Steve Buscemi" !! 6 ``` yields ```'B'```  
  - ```[9.4,33.2,96.2,11.2,23.25] !! 1 ``` yields ```33.2```
- Comparing Lists: Lists can be compared if their contents can be compared (<, <=, >, >=).
    -
### Two techniques for dealing with lists
1. Use library functions and operators
2. Use recursion with basic operations (head, tail, cons)

### List Comprehensions
- A way to create new lists based on other ones, like mathematical set notation.
- Example: set of all even numbers:
  - ```[x + 1|x<-[1,2,3,4]]```
  - ```[x*2 | x <- [1..10]]``` returns ```[2,4,6,8,10,12,14,16,18,20]  ```
  - ```[x*2 | x <- [1..10], x*2 >= 12]``` returns ```[12,14,16,18,20]  ```
  - ```[ x | x <- [50..100], x `mod` 7 == 3] ``` returns ```[52,59,66,73,80,87,94]   ```
  - ```boomBangs xs = [ if x < 10 then "BOOM!" else "BANG!" | x <- xs, odd x]```
      - ```boomBangs [7..13]``` returns ```["BOOM!","BOOM!","BANG!","BANG!"]```  

##### Week 4 Lecture 1, January 29 2018

WE HAD A TEST

##### Week 4 Lecture 2, February 1 2018

### Lazy Evaluation (Or just Clever Evaluation)
Recall this example from a previous lecture:
```
prime1 :: Int -> Bool
prime1 n = not (hasFactor n 2)
  where
  -- has factor means n

```

New version:
```
prime2 :: Int -> Bool
prime2 n =
  null [fact | fact <- [2 .. (intRoot n)], mod n fact == 0]
```
Is this more or less efficient? It's actually just as efficient as the previous version.

```
-- In prelude:
null :: [a] -> Bool
null [] = True
null (_:_) = False
```
Version 3:
```
prime3 :: Int -> Bool
prime3 n =
  [fact | fact <- [2 .. (intRoot n)], mod n fact == 0] == []
```
This depends on how list equality test works:
```
[] == [] = True
(x:xs) == (y:ys) = x == y && xs == ys
_ == _ = False
False && _ = False
True && x = x
```

Version 4:
```
prime4 :: Int -> Bool
prime4 n =
  length [fact | fact <- [2 .. (intRoot n)], mod n fact == 0] == 0
  -- we would have to count the num of elements in the entire list. In terms of
  -- execution, this is a lot slower
```

## Tuples
- Tuples are used when you know exactly how many values you want to combine and its type depends on how many components it has and the types of the components. They are denoted with parentheses and their components are separated by commas.
- They don't have to be homogenous. Unlike a list, a tuple can contain a combination of several types.
- Think about how we'd represent a two-dimensional vector in Haskell. One way would be to use a list. That would kind of work. So what if we wanted to put a couple of vectors in a list to represent points of a shape on a two-dimensional plane? We could do something like ```[[1,2],[8,11],[4,5]]```. The problem with that method is that we could also do stuff like ```[[1,2],[8,11,5],[4,5]]```, which Haskell has no problem with since it's still a list of lists with numbers but it kind of doesn't make sense.
- But a tuple of size two (also called a pair) is its own type, which means that a list can't have a couple of pairs in it and then a triple (a tuple of size three), so let's use that instead. Instead of surrounding the vectors with square brackets, we use parentheses: ```[(1,2),(8,11),(4,5)]```. What if we tried to make a shape like ```[(1,2),(8,11,5),(4,5)]```? Well, we'd get a "couldn't match expected type"
- Because of this, you should use tuples when you know in advance what data you're handling and if you need more rigidity
- Tuples can be compared if their components can be compared, but you cannot compare them if the tuples are of different size

```
type Triple = (Int, String, Float)

f :: Triple -> Float
-- give names to all three elements of the triple
f (a,b,c) = a + length b + c

-- Common use of tuples: combining related values. Represent course information
-- as a list of (String, Int) pairs
type CourseData = [(String, Int)]
testCourse :: CourseData
testCourse = [("Peter", 97), ("Susan", 78), ("Edmund", 50), ("Lucy", 97), ("Peter", 80)]

names :: CourseData -> [String]
names [] = []
names ((name, mark):moreData) = name:tailNames
  where tailNames = names moreData
```
uh blanked out from 10:02 to 10:11

Tuple Operations:
- Pair operations:
  - ```fst``` = gives first element of two element tuple
  - ```snd``` = gives second element of two element tuple
- ```zip``` = takes in two lists and returns the a list of tuple pairs of them
  -  ```zip [1,2,3,4,5] [5,5,5,5,5]```  yields ```[(1,5),(2,5),(3,5),(4,5),(5,5)]  ```
  - ```zip [1 .. 5] ["one", "two", "three", "four", "five"] ``` yields ```[(1,"one"),(2,"two"),(3,"three"),(4,"four"),(5,"five")]  ```
  - The longer list simply gets cut off to match the length of the shorter one
    - ```zip [1..] ["apple", "orange", "cherry", "mango"]``` yields ```[(1,"apple"),(2,"orange"),(3,"cherry"),(4,"mango")]  ```
