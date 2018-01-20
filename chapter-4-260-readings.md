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
[CISC 260 Notes](cisc260.md) //
[All Notes](http://karishmadaga.com/course-notes) // [About](http://karishmadaga.com)

# Chapter 4 Readings
* [4.1: Designing a Program in Haskell](#design)
* [4.2: Solving a Problem in Steps](#solve)
* [4.3: Enumerated Types](#enum)
* [4.4: Recursion](#recursion)
* [4.5: Primitive Recursion in Practice](#primitive)
* [4.6: Extended Exercise](#extended)
* [4.7: General Forms of Recursion](#general)
* [4.8: Program Testing](#testing)

<h2 id = "design">4.1: Designing a Program in Haskell</h2>
* Important questions to wonder when designing programs:
  * what does the program need to do?
  * what are the types of input (and then the expected output) that the program may be given?
  * What do I already now (definitions or functions already written, library and package functions, etc) and how can I use it in the definition of the new function?
  * Can I break the problem down into simpler parts? (divide and conquer)
    * What if I had any functions I wanted: which could I use in writing the solution?

<h2 id ="solve">4.2: Solving a Problem in Steps, local definitions</h2>
#### Local definition: can only be used in the definition of a function, and nowhere else
Local definitions can help us simplify the code, e.g.:
```
fourPics :: Picture -> Picture

fourPics pic =
  left 'beside' right
    where
      left = pic 'above' invertColour pic
      right = invertColour (flipV pic) 'above' flipV pic

```

We can also define a **local function**.
```
fourPics :: Picture -> Picture

fourPics pic =
  left 'beside' right
    where
      -- stack puts a picture above its inverted version. Then use stack to define
      -- left and right parts of the picture
      stack p = p 'above' invertColour p
      left = stack pic
      right = stack (invertColour (flipV pic))
```
### Let Expressions
It is also possible to make definitions local to an expression, rather than local to a function clause as for ```where```. For example, we can write:
```
let x = 3 + 2 in x^2 + 2*x - 4
```
If more than one definition is included in one line, they need to be separated by semicolons.
```
let x = 3 + 2, y = 5 - 1 in x^2 + 2*x - y
```
We tend to use these only occasionally.

### Scopes
A Haskell script consists of a sequence of definitions. The **scope** of a definition is the part of the program in which the definition can be used. All definitions at the top-level in Haskell have their scope as the whole script they are defined in: that is, they can be used in all the definitions the script contains, even be used in definitions which occur before theirs in the script. Local definitions, given by ```where``` clauses, are not supposed to be visible in the whole script. The same is true of the variables in a function definition.

<h2 id ="enum">4.3: Enumerated Types</h2>

### Data Types of Haskell
Suppose we want to model rock, paper, scissors in a program.
```
data Move = Rock | Paper | Scissors
            deriving (Show, Eq)
            -- above line allows us to compare the elements of this type for equality (Eq) and also to be able to see them printed out (Show)

-- defining basic functions using the Move type
beat :: Move -> Move

beat Rock = Paper
beat Paper = Scissors
beat Scissors = Rock

lose :: Move -> Move

lose Rock = Scissors
lose Paper = Rock
lose _ = Paper
-- the wildcard '_' instead of Scissors in the final clause is used because this clause is only matched when the others don't, and this will only happen for the value Scissors
```
<h2 id ="recursion">4.4: Recursion</h2>
Recall: Recursion is in which the definition of a function or other object refers to the object itself

#### Example: A Story about Factorials
Factorial: the factorial of a natural number is the product of all natural number from one up to (& including) that number

```
factorial :: Integer -> Integer
factorial n
  | n < 0 = error "enter a natural number"
  | n == 0 = 1
  | n > 0 = factorial (n - 1) * n

```
<h2 id ="primitive">4.5: Primitive Recursion in Practice</h2>
The pattern of primitive recursion says that we can define a function from the natural numbers 0, 1, ... by giving the value at zero and by explaining how to go from the value at n - 1 to the value n.

```
function n
  | n == 0 = ...
  | n > 0 = ... function (n - 1) ...
```

```
regions :: Integer -> Integer
regions n
  | n == 0 = 1
  | n > 0 = regions (n - 1) + n

```
