
## Introduction

> Beautiful is better than ugly.  
> Explicit is better than implicit.  
> Simple is better than complex.  
> Complex is better than complicated.  
> Flat is better than nested.  

<a href="https://www.python.org/dev/peps/pep-0020/"><img alt="The Zen of Python (excerpt), Tim Peters (2004)" align="right"/><a/><br/>



**Contents**
* [Objectives](#objectives)
* [First steps ](#first-steps-) <img src="https://img.shields.io/badge/-Duration:_30mn-black.svg?style=flat-square" align="right"/>

* [Types & variables]() .................................................................................................................................. <img src="https://img.shields.io/badge/-Duration:_30mn-black.svg?style=flat-square" align="right"/>
* [Control flow]() ........................................................................................................................................... <img src="https://img.shields.io/badge/-Duration:_30mn-black.svg?style=flat-square" align="right"/>
* [Functions]() ............................................................................................................................................... <img src="https://img.shields.io/badge/-Duration:_30mn-black.svg?style=flat-square" align="right"/>
* [Modules]() ................................................................................................................................................. <img src="https://img.shields.io/badge/-Duration:_30mn-black.svg?style=flat-square" align="right"/>
* [Input / Output]() ........................................................................................................................................ <img src="https://img.shields.io/badge/-Duration:_30mn-black.svg?style=flat-square" align="right"/>
* [Exceptions]() ............................................................................................................................................. <img src="https://img.shields.io/badge/-Duration:_30mn-black.svg?style=flat-square" align="right"/>


<br/><br/>

## Objectives

The primary goals of this lesson are:

* To introduce Python types & manipulations
* To start programming moderately complex scripts
* To be able to read and write files 
  


<br/><br/>
## First steps <img src="https://img.shields.io/badge/-Duration:_90mn-black.svg?style=flat-square" align="right"/>

Now it's time to experience a little bit with Python. Let's start with simple
arithmetic operations because Python can be used as a regular calculator with
standard arithmetic operations (addition, subtraction, multiplication,
division, etc.)

#### Addition

```pycon
>>> 2 + 3
5
```

#### Subtraction

```pycon
>>> 11 - 3
8
```

#### Multiplication

```pycon
>>> 3 * 4
12
```

#### Division

```pycon
>>> 11 / 5
2.2
```

#### Integer division

```pycon
>>> 11 // 5
2
```

#### Modulo operation

```pycon
>>> 11 % 5
1
```

#### Power

```pycon
>>> 2**3
8
```

Note that you cannot have spaces between digits of a number:

```pycon
>>> 1 0 + 2 
  File "<stdin>", line 1
    1 0 + 2
      ^
SyntaxError: invalid syntax
```

In such a case, Python complains about a syntax error and points at the
position of the error in the expression (using the `^` character). Why Python
points at the zero and not the space ? Because you could have written `1 + 2`
and the space would have been legal. The interpreter can only find the error
after it discovers the extra digit and consequently points at it when reporting
the error.

Of course, you can compose any number of operations in order to compute a more
complex operation:

```pycon
>>> 11 - (5 * (11//5)) #  = 11 % 5
1
```


###  Native numeric types

Python offers natively four main native numeric type, `bool`, `integer`,
`float` and `complex`. But always keep in mind that they are the poor's man
version of their mathematical equivalent (Boolean (𝔹), Integer (ℤ), Real (ℝ)
and Complex (ℂ)): `ìnteger` have limited range, `float` and `complex` have
limited range and precision.

In the case of `float` and `complex`, this has very important consequences.

``` pycon
>>> 0.1 + 0.1 + 0.1 == 0.3
False
```

The reason is that decimal numbers `0.1` and `0.3` cannot be represented
exactly and are only approximated. On most machines, if Python were to print
the actual value of the approximation, it would have to display:

```pycon
>>> print("{0:.64f}".format(0.1))
0.1000000000000000055511151231257827021181583404541015625000000000
>>> print("{0:.64f}".format(0.3))
0.2999999999999999888977697537484345957636833190917968750000000000
```

Consequently, Python (as many other languages) chose to display a rounded value
instead. If you want to know more, have a look at the [Floating Point
Arithmetic: Issues and
Limitations](https://docs.python.org/3/tutorial/floatingpoint.html) chapter in
the official [Python 3
tutorial](https://docs.python.org/3/tutorial/index.html). An immediate and
practical consequence is that what you see in the console is not always what
you get in memory, even if they're reasonably close. If you want to know more
about that, make sur to read [What Every Computer Scientist Should Know About
Floating-Point
Arithmetic](https://docs.oracle.com/cd/E19957-01/806-3568/ncg_goldberg.html),
David Goldberg, Computing Surveys, 1991.


The right way to compare float numbers is thus to check if the difference is
below a given threshold:

``` pycon
>>> (0.1 + 0.1 + 0.1) - 0.3 < 1e-15
True
```


For each type, there exist many ways to specify the same number.

``` pycon
>>> True              # Boolean
>>> 0b1010            # Integer (base  2: binary)
>>> 0o12              # Integer (base  8: octal)
>>> 10                # Integer (base 10: decimal)
>>> 0x0a              # Integer (base 16: hexadecimal)
>>> 10.0              # Float
>>> 1e1               # Float (scientic notation)
>>> float('inf')      # Float (infinity +∞)
>>> float('nan')      # Float (Not A Number: nan)
>>> 10 + 0j           # Complex
```

You can also force the type of a quantity by casting it into a different type:

```pycon
>>> bool(0)
False
>>> int(0)
0
>>> float(0)
0.0
>>> complex(0)
0j
```


### Beyond simple arithmetic

If you want to use more elaborate functions, you'll need the help of the
[mathematical module](https://docs.python.org/3/library/math.html) for real
numbers and the [complex mathematical
module](https://docs.python.org/3/library/cmath.html) for complex numbers. To
do that, we have to `import` a library and to use its name as a prefix, in
front of the functions we want to use. For those who know Python, you might
have been tempted to write `from math import *` but this is almost always a bad
idea.


**Power and logarithmic functions** 

```pycon
>>> import math
>>> math.log( math.exp( 1.234 ) )
1.234
```

**Trigonometric functions**

```pycon
>>> import math
>>> math.asin( math.sin( 1.234 ) )
1.234
```

**Hyperbolic functions**

```pycon
>>> import math
>>> math.asinh( math.sinh( 1.234 ) )
1.234
```

**Special functions**

```pycon
>>> import math
>>> math.gamma( 2.0 )
1.0
```

**Constants**

```pycon
>>> import math
>>> math.pi
3.141592653589793
>>> math.e
2.718281828459045
>>> math.nan # Not A Number
nan
>>> math.inf # Infinite
inf
```


### Logical operations

Logic is an important part of Python because this allows to manipulate and
compare quantities, including numbers, and we'll see later that it works for
all kind of objects.

```pycon
>>> True and True # Logical and
>>> 42 or 57      # Logical or
>>> 1 == 2-1      # Equality test
>>> 1 != 2        # Inequality test
>>> 1 is 2-1      # Identity test
>>> not 24        # Negation
```

Note that the `is` keyword really means identity (the two terms point to the
same object), it is not a test for equality.

```pycon
>>> 1 is 1.0
False
>>> True is 1
False
>>> True and 1
True
```

### Bitwise operations

Bitwise operations are logical operations that operate a the bit level. They
might be useful in some situations but we won't use them much in this course.

```pycon
>>> 1 | 2   # bitwise or
>>> 1 & 2   # bitwise and
>>> 1 ^ 2   # bitwise xor
>>> 8 << 2  # bitwise left shift
>>> 8 >> 2  # bitwise right shift
>>> ~8	  # bitwise negation
```



<br/><br/>
## Exercises

Before moving to the [next lesson](02-introduction.md), here are some simple
exercises that should take you only a few minutes to solve. If you want the
solution, just type these expression in a Python console.


### Find the type of the following expressions

```
.0
-1
1,
'float(4) + 5'
1e2
1j
math.nan
```

### Are these legal Python expressions?

```
1 + 1 == 2
1 = 2
1 + 1i
1 <- 2
0.+.0
3***3
3 <<2>> 3
```

### Find the result of the following expressions

```
1.+.1
0b1+0xb1
(1,)*3
1e1000 - 1e1000
'abc'*3
3 or 10
3 <2 > 3
```


<br/>

<br/><br/>

## Basic types <img src="https://img.shields.io/badge/-Duration:_30mn-black.svg?style=flat-square" align="right"/>




Beside being a convenient calculator, Python is also (and mostly) a powerful
programming language with an elegant and intuitive syntax. Furthermore, you
have to knwo that Python is an interpreted langage, meaning each time you enter
a set of instructions, they need to be intepreted by the Python interpreter. This
can make Python quite slow in some situation but we'll later how to overcome most
of Python slowness.

### Variables

Until now, we have been playing in the console, throwing some expressions in
the interpreted and checked the result. Problem is that those expression cannot
be re-used. It's thus time to save us some trouble and assign those expressions
to variables. This can be done quite naturally.

``` python
>>> width = 1
>>> height = 2
```

What is really cool though is that you can assign several variables at once:

``` python
>>> width, height = 2,1
>>> width
1
>>> height
2
```

However, you cannot refer a new variable on the same line

``` python
>>> width, height = 2, 2*width
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'width' is not defined
```

In this case, you have to split the expression in two distinct lines.

``` python
>>> width = 2
>>> height = 2*width
```

Variables can be manipulated just as any expression but they need to have been
defined previously.

``` python
>>> a = 2*b
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'b' is not defined
```

In interactive mode, that is, the console mode we've been using from the start,
there is a special variable whose name is '_' and that contains the last
**printed** expression.

``` python
>>> very_long_name = 10
>>> very_long_name
10
>>> b = 2 + _ # here, _ = very_long_name
>>> b
12
```

Don't assign explicitely a value to the `_` variable or you'll kill the magic,
and you don't want to do that, do you ?



### Containers

Beside the numeric types, Python also offers native container type (also known
as collections), one is dedicated to the storing of ordered sequence of
characters (i.e. strings) while some others allows to store just anything and
offers different properties. In a nutshell:

``` python
>>>  "1,2,3,4"  # String (ordered, character only, immutable, indexable)
>>>  (1,2,3,4)  # Tuple (ordered, immutable, indexable)
>>>  [1,2,3,4]  # List (ordered, mutable, indexable)
>>>  {1,2,3,4}  # Set (unordered, mutable, unique elements)
>>>  {1:2,3:4}  # Dictionnary (unordered, mutable, hashable)
```

**Strings**

Strings are expressed by enclosing a text using pairs of " or \'
characters. Depending on the character you chose, you can use the other inside
the string.

``` python
>>> "Hello 'world!'"
"Hello 'world!'"
>>> 'Hello "world"!'
'Hello "world!"'
>>> "" # empty string
''
```

Note that you can split a string using spaces and Python will concatenate all
the pieces together.

``` python
>>> "Hello"  " "  "world!"
'Hello world!'
```


But you can also explicitely concatenate the different pieces together.

``` python
>>> "Hello" + " " + "world!"
'Hello world!'
```

For multiline strings, you need to triple the enclosing quotes or to use parentheses.

``` python
>>> """Hello 
... world!"""
'Hello\nworld!'

>>> '''Hello 
... world!'''
'Hello\nworld!'

>>>("Hello"
... " world!")
'Hello world!'
```

In the output above, you can seen the "\n" character has been added, it
expresses the newline character. There are several backslashed characters:

Escape Sequence | Meaning 
----------------|---------------------------
\\\\            | Backslash (\)
\\\'            | Single quote (')
\\\"            | Double quote (")
\a              | ASCII Bell (BEL)
\b              | ASCII Backspace (BS)
\n              | ASCII Linefeed (LF)
\r              | ASCII Carriage Return (CR)
\t              | ASCII Horizontal Tab (TAB)
\v              | ASCII Vertical Tab (TAB)

This means the '\n' will be interpreted as a new line character, but what if we
want to really have '\n' in our string as in 'C:\\some\\name'? Either we
"escape" all the backslash or we prefix the string with `r` meaning special
characters won't be interpeted.

``` python
>>> print('C:\some\name')
'C:\some
ame'
>>> print('C:\\some\\name')
C:\some\name
>>> print(r'C:\some\name')
C:\some\name
```

Strings in Python 3 are encoded using UTF-8 ([Unicode]), meaning you can encode
pretty much any glyphs fom any languages (and emojis as well).

``` python
>>> "ℕ ⊂ ℤ ⊂ ℚ ⊂ ℝ ⊂ ℂ" 
'ℕ ⊂ ℤ ⊂ ℚ ⊂ ℝ ⊂ ℂ'
```

**Tuples**

Tuples are immutable containers, meaning they cannot be changed after they've
been created. They allow to store pretty much anything, including other tuples.
To create a tuple, you simply write a comma-separated list of values,
optionally enclosed by parentheses.

``` python
>>> 1,2,3
(1, 2, 3)
>>> 1, "2", (1,2) 
(1, '2', (1, 2))
>>> () # empty tuple
()
```

**Lists**

Lists are mutable containers quite similar to tuple, but they can be modified
after creation. They also allow to store pretty much anything. To create a
list, you need to write a comma-separated list of values enclosed by square
brackets.

``` python
>>> [1,2,3]
[1, 2, 3]

>>> [1, "2", (1,2)]
[1, '2', (1, 2)]

>>> [] # empty list
[]
```

**Sets**

Sets are mutable containers (they can be modified) and contains only unique
elements, i.e. they prevent to have duplicated elements.

``` python
>>> {1, 2, 2}
{1, 2}

>>> {1, 2, "2"}
{1, 2, '2'}
```

**Dictionnary**

Dictionnary can be considered as a kind of associative memory where items are
indexed by a key (instead of integer). The type of the key can be pretty much
anything.

``` python
>>> { "item 1" : 1, "item 2" : 2}
{'item 2': 2, 'item 1': 1}
>>> { 1 : 2, 3 : 4}
{1: 2, 3: 4}
```


### Indexing and slicing

Individual items of a list, tuple and strings can be accessed invidually using
their position as index. Note that first element has index 0

``` python
>>> d = [1,2,3,4,5]
>>> d[0]
1
```

This also work using negative indices, meaning the position has to be taken
from the end. Note that last element has index -1.

``` python
>>> s = "Hello world!"
>>> s[-1]
'!'
```

Furthermore, we can also access a **range** of items using the slice notation
`start:end`. Note that both start and end are optional.

``` python
>>> d = [1,2,3,4,5]
>>> d[1:3]
[2, 3]
```

If start is missing, Python will implicitly replace it by the start of the
list. If end is missing, Python will implicitly replace it by the end of the
list.


``` python
>>> d = [1,2,3,4,5]

>>> d[1:]
[2, 3, 4, 5]

>>> d[:2]
[1, 2]

>>> d[:]
[1, 2, 3, 4, 5]
```

We can further refine our slice by giving the step to between elements. The new
syntax is thus `start:end:step`.

``` python
>>> d = [1,2,3,4,5,6]
>>> d[0:5:2]
[1, 3, 5]

# Can be abbreviated into
>>> d[::2] # 
[1, 3, 5]
```

What if we use a negative step? We get the reversed sequence.

``` python
>>> d = [1,2,3,4,5,6]
>>> d[::-1] 
[6, 5, 4, 3, 2, 1]
```

Because strings are indexable, indexing and slicing work just the same.


``` python
>>> s = "Hello world!"
>>> s[6:-1]
" world"
>>> s[6:]
" world!"
```


### Adding and removing

Adding an element to a mutable container can be done in two distinct
ways. Either by creating a new container that is the container plus the new
item, or by inserting the new item into the container, hence modyfying it.

``` python
>>> l1 = [1, 2, 3]
>>> l2 = l1 + [4]
>>> l2
[1, 2, 3, 4]
>>> l1.append(4)
>>> l1
[1, 2, 3, 4]
```

For removing items, we need to use the **del** keyword and give indices where
to delete items.

``` python
>>> l1 = [1, 2, 3, 4, 5, 6]
>>> del l1[0 ]
>>> l1
[2, 3, 4, 5, 6]
```

But we can also delete a range of indices at once.

``` python
>>> l1 = [1, 2, 3, 4, 5, 6]
>>> del l1[::2]
>>> l1
[2,4,6]
```

Something you will discover soon enough (or maybe you've already discovered it)
is that Python is rather nitpicking about indentation.

``` python
>>> a = 1
>>>  a = 1
  File "<stdin>", line 1
    a = 1
    ^
IndentationError: unexpected indent
```

The reason is that indentation has a semantic meaning but we'll see that later.




### Exercises




### Find the result of the following expressions

```
1.+1,
1,+1.
(1,)*3
1e1000 - 1e1000
'abc'*3
3 or 10
3 <2> 3
```
<details><summary>
Click to see solution
</summary></p>

```
1.+1,            # (2.0,)
1,+1.            # (1, 1.0)
(1,)*3           # (1, 1, 1)
1e1000 - 1e1000  # nan
'abc'*3          # 'abcabcabc'
3 or 10          # 3
3 <2> 3          # False
```


</details>

### How to...

<details><summary>
... build the empty set?
</summary></p>

```Python
empty = {}    # Wrong: this builds an empty dictionnary
empty = set() # Right
```
</p>
</details>


<details><summary>
... get the list of unique letters composing "abracadabra"?
</summary></p>

```Python
letters = set("abracadabra")
```
</p></details>


<details><summary>
... build a tuple of two empty lists?
</summary></p>

```Python
a = ([], []) # Right but parenthesis are not necessary
a = [], []   # Right
```
</p></details>


<details><summary>
... generate a list of all even numbers between 20 and 40 (included)?
</summary></p>

```Python
numbers = list(range(20, 41, 2)
```
</p></details>

<details><summary>
... check if a word is a palindrom?
</summary></p>

```Python
word = "kayak"
print(word == word[::-1]) # Note that this does not work with "Kayak"

word = "Kayak".lower()
print(word == word[::-1]) # This works thanks to the lower method
```
</p></details>

<details><summary>
... transform the string "1.2" into a float?
</summary></p>

```Python
a = float("1.2)
```
</p></details>

<details><summary>
... count the number of unique elements in a list?
</summary></p>

```Python
mylist = [1,2,3,4,3,2,1]
size = len(set(mylist))
```
</p></details>

<details><summary>
... print the string `"Isn't it, he said"` (including quotes)?
</summary></p>

```Python
print('''"Isn't it, he said"''')
```
</p></details>

<details><summary>
... swap the content of two variables?
</summary></p>

```Python
a,b = 1,2
a,b = b,a
```
</p></details>


<br/><br/>
## Bibliography


Here are a set of resources for those who want to go further in their knowledge
of Python.

* [**The (official) Python tutorial**](https://docs.python.org/3/tutorial/index.html)
  does not attempt to be comprehensive and cover every single feature, or even
  every commonly used feature. Instead, it introduces many of Python's most
  noteworthy features, and will give you a good idea of the language's flavor
  and style.

* [**Dive into python**](http://www.diveintopython3.net) is a teach-by-example
  guide to the paradigms of programming in Python and modern software
  development techniques. It assumes some preexisting knowledge of programming,
  although not necessarily in Python.  
  

<br/><br/>
---

Copyright © 2019 [Nicolas P. Rougier](http://www.labri.fr/perso/nrougier) •
Released under a [CC-BY 4.0 International](https://creativecommons.org/licenses/by/4.0/legalcode) license.
