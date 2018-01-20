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

# CISC 221: Data Representations Readings
Since the structure of the course is flipped, a majority of the learning is through readings. Chapter 2 covers data representation.
See the notes [here](cisc221week2r.md) or below:

### Data Representation
* bits: values of 0 or 1
* decimal system: base 10

When we group bits together and apply some interpretation that gives meaning to the different possible bit sequences, we can represent the elements of any finite set.

### Three of the Most Important Number Representations:
* Unsigned Encodings: for n∈ℕ (n ≥ 0)
* Two's Complement Encodings: the most common way to represent signed integers. x∈Z (limited to be between positive and negative 2,147,483,647).
* Floating Point Encodings: The base 2 version of scientific notation for representing real numbers (recall: real numbers are the missing values from the set of all rational values).

Overflow: operations can overflow when the results are too large to be represented

## 2.1 Information Storage

* Some terminology:
  * byte: smallest addressable unit of memory, 8 bits long
  * virtual memory: a machine level program views the memory as a very large array of bytes, referred to as the virtual memory.
  * address: every byte of memory has a unique address number, called the address
  * virtual address space: set of all possible memory addresses (conceptual)
    * In reality, it is a combination of:
      * RAM
      * disk storage
      * special hardware
      * OS software
    * Example: the value of a _pointer_ in C - whether it points to an integer, struct, or other program object -
is the virtual address of the first byte of some block of storage

### 2.1.1 Hexadecimal Notation
How can we easily/compactly store the value of a byte (8 bits)?
1. Binary notation: value ranged from 0000 0000 to 1111 1111.
2. Decimal Integer: value ranges from 0 (base 10) to 255 (base 10).
Neither are convenient.

#### Hexadecimals
* used digits 0 - 9 and characters A - F to represent the 16 possible values. Value range: 00 (base 16) to FF (base 16)
* In C, _numeric constants_ starting with 0x or 0X are interpreted as hexadecimals

#### Converting Between Representations of Bit Patterns

Hexadecimal | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | A | B | C | D | E | F
--- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | ---
**Decimal** | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15
**Binary**  | 0000 | 0001 | 0010 | 0011 | 0100 | 0101 | 0110 | 0111 | 1000 | 1001 | 1010 | 1011 | 1100 | 1101 | 1110 | 1111

Example: 0x39A7F8 to binary: 0011 1001 1010 0111 1111 1000

Trick with Hexadecimals and the Powers of 2:
If x is a power of 2 such that x = 2^n where n > 0, we can find the hexadecimal representation of it.

Example: x = 2048 = 2^11. n = 11 = 3 + 4*2. n can be written in the form i + 4j where 0 <= i <= 3. We can write x with a leading hex digit of 1 (i = 0), 2 (i = 1), 4 (i = 2), or 8 (i = 3).

#### Decimal number to Hexadecimal

x = 16q + r. Use r as the least significant digit and repeat the process on q.

Example: 314156

315156 = 16 (**19634**) + (**12**) --> **C**

19634 = 16 (**1227**) + (**2**) --> **2**

1227 = 16 (**76**) + (**11**) --> **B**

76 = 16 (**4**) + (**12**) --> **C**

4 = 16 (0) + **4** --> **4**

Therefore, 315156 is ```0x4CB2C```

#### Hexadecimal to Decimal
Ex: ```0x7AF```

Compute by multiplying each hexadecimal by the appropriate power of 16.

7 * 16^2 + 10 * 16 + 15 = 1967

### Endianness
Consider a _w_-bit integer having a bit representation [X_w-1, X_w-2, ..., X_o]. Assuming _w_ is a multiple of 8, the bits can be grouped into bytes with the most significant byte having bits [X_w-1, ... , X_w-8] and the least significant having [X_7, ... , X_o].

#### Little Endian: least significant byte comes first (so the most significant is at the last memory addresses).
[X_7, ... , X_o], ... , [X_w-1, ... , X_w-8].

Intel machines are normally little-endian.

#### Big Endian: Most significant at the first memory address [X_w-1, ... , X_w-8], ... , [X_7, ... , X_o].

Example: int x has a hexadecimal value of 0x01234567

Type | 0x100 | 0x101 | 0x102 | 0x103
--- | --- | --- | --- |
Big Endian | 01 | 23 | 45 | 67
Little Endian | 67 | 45 | 23 | 01

When everything works as it should, byte ordering is not an issue. It becomes a problem when:
1. Binary data is communicated over a network between different machines (i.e. little endian machine sends data to big endian machine)
2. Byte sequences representing integer data
3. Programs are written to circumvent the normal type system

### 2.1.8 Bit Level Operations in C
Bitwise boolean operations can be applied to any 'integral' data type, i.e. type char or integer.

Example:

C Expression | Binary Expression | Binary Result | Hexadecimal Result
--- | --- | --- | --- |
~0x41 | ~[0100 0001] | [1011 1110] | 0xBE
~0x00 | ~[0000 0000] | [1111 1111] | 0xFF
0x69 & 0x55 | [0110 1001] & [0101 0101] | ... | 0x41
0x69/0x55 | [0110 1001]/[0101 0101] | ... | 0x7D

Note: the / is meant to be a bitwise OR, but markdown separates strings into separate cell when there is a '|'.

#### Masking Operations
Bit pattern that indicates a selected set of bits within a word.

Example: ```0xFF``` (having ones for the least significant bits) indicates the low order byte of a word.

Bit level operation: ```x & 0xFF``` --> Returns the value consisting of the least significant byte of x, but with all other bytes set to 0.

Example: let int x = 0x089ABCDEF. ```x & 0xFF``` --> ```0x000000EF```

Example: ```~0 ```(bitwise not)-> mask of _all_ the ones, regardless of the word size.

### 2.1.9 Logical Operators in C
* Logical Operators: ```||``` (logical OR), ```&&``` (logical AND), and ```!``` (logical NOT)
* Treat any nonzero argument representing TRUE and argument 0 as representing FALSE. 1 -> T and 0 -> F.
* Logical operators (compared to their bitwise counterparts) do not evaluate their second argument if the result of the expression can be determined by evaluating the first argument
  * Example: ```a && 5/a``` will never cause division by 0
  * Example: ```p && * p++``` will never cause dereferencing of a null pointer

### 2.1.10 Shift Operations in C
C also provides a set of shift operations for shifting bit patterns to the left and to the right. For an operand x having a bit representation [X_n-1, X_n-2, ..., X_o], the C expression ```x << k``` yields a value with bit representation [X_n-k-1, X_n-k-2, ..., X_o, 0,...,0]. X is shifted _k_ bits to the left, dropping off the k most significant bits and filling the right end with _k_ zeroes. The shift amount should be between 0 and n-1. Shift operations associate from left to right, so x << j << k  = (x << j) << k.

The corresponding right shift operation ```x >> k``` has a slightly subtle behaviour. Machines support two forms of right shift: **logical** and **arithmetic**.

* An _arithmetic_ right shift fills the left end with _k repetitions_ of the _most significant bit_.
* A _logical_ right shift fills the left end with _k_ zeroes.

For unsigned data, right shifts must be logical. However, for unsigned data, it could be either arithmetic or logical. In practice, almost all compiler/machine combinations use arithmetic right shifts for signed data. Java is specific. ```x >> k``` shifts x **arithmetically** by k positions and ```x >>> k``` shifts x **logically** by k positions.

## 2.2 Integer Representations
In 2.2, we describe two different ways bits can be used to encode integers. Unsigned can only represent nonnegative numbers and Signed can represent the entire set of integers.

Typical ranges for C integral data types on a 32-bit machine

C Data Type | Minimum | Maximum
--- | --- | --- |
char | -128 | 127
unsigned char | 0 | 255
short [int] | -32768 | 32767
unsigned short [int] | 0 | 65535
int | −2,147,483,648 | 2,147,483,647
unsigned [int] | 0 | 4,294,967,295
long [int] | −2,147,483,648 | 2,147,483,647
unsigned long [int] | 0 | 4,294,967,295
long long [int] | -9,223,372,036,854,775,808 | 9,223,372,036,854,775,807
unsigned long long [int] | 0 | 18,446,744,073,709,551,615

### 2.2.1 Integral Data Types
C supports a variety of integral data types - ones that represent finite ranges of integers.

The number of bytes allocated for the different sizes vary according the machine's word size and the compiler. Most 64-bit machines use an 8-byte representation compared to the 4-byte representation on 32-bit machines. Note: the range of negative numbers extend one further than the range of the positive numbers.

### 2.2.2 Unsigned Encodings


### 2.2.3 Two's Complement Encodings
* Two's complement is the most common representation to represent the entire set of integers (so it includes negative values)

### 2.2.4 Conventions between Signed and Unsigned
* covers casting rules

### 2.2.5 Signed vs Unsigned in C

### 2.2.6 Expanding the Bit Representation of a Number

### 2.2.7 Truncating Numbers

### 2.2.8 Advice on Signed vs Unsigned


## 2.3 Integer Arithmetic

### 2.3.1 Unsigned Addition

### 2.3.2 Two's Complement Addition

### 2.3.3 Two's Complement Negation

### 2.3.4 Unsigned Multiplication

### 2.3.5 Two's Complement Multiplication

### 2.3.6 Multiplying by Constants

### 2.3.7 Dividing by Powers of 2

## 2.4 Floating Point

### 2.4.1 Fractional Binary Numbers

### 2.4.2 IEEE Floating-Point Representation

### 2.4.3 Example Numbers

### 2.4.4 Rounding

### 2.4.5 Floating-Point Operations

### 2.4.6 Floating Point in C
