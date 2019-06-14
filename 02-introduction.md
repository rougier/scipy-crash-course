
## Introduction

> Beautiful is better than ugly.  
> Explicit is better than implicit.  
> Simple is better than complex.  
> Complex is better than complicated.  
> Flat is better than nested.  

<a href="https://www.python.org/dev/peps/pep-0020/"><img alt="The Zen of Python (excerpt), Tim Peters (2004)" align="right"/><a/><br/>



**Contents**
* [Objectives](#objectives)
* [Types & variables]() ....................................................................................................................................
  <img src="https://img.shields.io/badge/-Duration:_30mn-black.svg?style=flat-square" align="right"/>
* [Control flow]() .............................................................................................................................................
  <img src="https://img.shields.io/badge/-Duration:_30mn-black.svg?style=flat-square" align="right"/>
* [Functions]() .................................................................................................................................................
  <img src="https://img.shields.io/badge/-Duration:_30mn-black.svg?style=flat-square" align="right"/>
* [Modules]() ...................................................................................................................................................
  <img src="https://img.shields.io/badge/-Duration:_30mn-black.svg?style=flat-square" align="right"/>
* [Input / Output]() ..........................................................................................................................................
  <img src="https://img.shields.io/badge/-Duration:_30mn-black.svg?style=flat-square" align="right"/>
* [Exceptions]() ...............................................................................................................................................
  <img src="https://img.shields.io/badge/-Duration:_30mn-black.svg?style=flat-square" align="right"/>


<br/><br/>

## Objectives

The primary goals of this lesson are:

* To introduce Python types & manipulations
* To start programming moderately complex scripts
* To be able to read and write files 
  


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
