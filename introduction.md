# A Gentle introduction to Python
**Nicolas P. Rougier** - [Nicolas.Rougier@inria.fr](mailto:Nicolas.Rougier@inria.fr)  
Lecture notes from the scientific Python crash course taught at the [University of Bordeaux] for the academic year 2021.  
This work is licensed under [Creative Commons Attribution 4.0 International
License](http://creativecommons.org/licenses/by/4.0/).


Objectives
-------------------------------------------------------------------------------

The primary goal of this lesson is twofold:

* To ensure you have a clean Python installation
* To discover Python basic syntax through the interpreter

**Note**: This lesson only covers the very basics of Python. If you're already
          familiar with Python, you can probably skip it and target the next
          lesson, but who knows, you might discover some tips while reading
          this lesson. In any case, make sure to have all necessary packages
          installed before the next lesson.



Installation
-------------------------------------------------------------------------------

As of today (2018), Python exists mainly in two flavors: Python 2.x and
Python 3.x.  On most system, a 2.x version is already installed and for some
systems, the 3.x is also installed. However, because we don't want to mess with
the system installation, we'll install our own private version usign either:

* Enthought [Canopy] is a comprehensive Python analysis environment that
provides easy installation of the core scientific analytic and scientific
Python packages, creating a robust platform you can explore, develop, and
visualize on.

* [Anaconda] by Continuum Analytics which is a completely free Python
distribution (including for commercial use and redistribution). It includes
more than 400 of the most popular Python packages for science, math,
engineering, and data analysis. 

For this lesson, we'll go for [Anaconda] that is available for several
architectures:

* [Anaconda for windows](https://www.anaconda.com/distribution/#windows)
* [Anaconda for linux](https://www.anaconda.com/distribution/#macos)
* [Anaconda for OSX](https://www.anaconda.com/distribution/#linux)

The anaconda comes with a lot of nice features but we won't use them (if you're
interested, have a look at their
[user guide](https://docs.anaconda.com/anaconda/user-guide/)). Next step is to
test the installation. To do that, you'll need to open a terminal and type:

``` bash
$ conda --version
conda 4.4.10
```

If this works, your conda version should be greater than 3.19.1.
We can now try to start the Python interpreter.

``` bash
$ python
Python 3.6.4 (default, Jan  6 2018, 11:51:59)
[GCC 4.2.1 Compatible Apple LLVM 9.0.0 (clang-900.0.39.2)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> |
```

The anaconda comes also with the [IPython] interpreter which is far more
powerful that the vanilla interpreter.


``` bash
$ ipython
Python 3.6.4 |Anaconda, Inc.| (default, Jan 16 2018, 12:04:33)
Type 'copyright', 'credits' or 'license' for more information
IPython 6.2.1 -- An enhanced Interactive Python. Type '?' for help.

In [1]: |
```

Now let's check our installation to see if everything is ok.  At this point, no
need yet to understand what you're typing but we need to check if some
important packages are present with the proper version. In the following
examples, the `>>>` is the prompt and does not need to be typed. For example,
if you chose the IPython interpetrer, you prompt is more likely something like
`[12]:`. There is also a second prompt (`...`) meaning the previous line is not
ended and needs to be terminated. This is for example the case when you enter an
parantheses unbalanced expression (i.e. number of opening parathenses is greater
than the number of closing parantheses).

**Checking for numpy**

``` python
>>> import numpy
>> print(numpy.__version__)
1.13.3
>>> numpy.test() # This can last a few seconds
..........................
```

**Checking for scipy**

``` python
>>> import scipy
>>> print(scipy.__version__)
0.19.1
>>> scipy.test() # This can last a few seconds
...........................
```

**Checking for matplotlib**

``` python
>>> import matplotlib
>>> print(matplotlib.__version__)
2.1.0
>>> matplotlib.test() # This can last a few minutes
...........................
```

**Checking for cython**

``` python
>>> import cython
>>> print(cython.__version__)
0.26
```

For each of these packages, the `x.y.z` version should be equal or greater than
the displayed version. If this is not the case, then maybe you conda
installation is not up to date. You can upgrade all packages at once using:

``` bash
$ conda update --all
```

If something goes wrong, you'll have to check on the
[Anaconda help page](https://docs.anaconda.com/).


Python is a calculator
-------------------------------------------------------------------------------

### Arithmetic computation

Now it's time to experience a little bit with Python. Let's start with simple
arithmetic operations because Python can be used as a regular calculator with
standard arithmetic operations (addition, subtraction, multiplication,
division, etc.)

Addition
``` python
>>> 2 + 3
5
```

Subtraction
``` python
>>> 11 - 3
8
```

Multiplication
``` python
>>> 3 * 4
12
```

Division
``` python
>>> 11 / 5
2.2
```

Integer division
``` python
>>> 11 // 5
2
```

Modulo operation
``` python
>>> 11 % 5
1
```

Power
``` python
>>> 2**3
8
```

Note that you cannot have spaces between digits of a number:

``` python
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

``` python
>>> 11 - (5 * (11//5)) #  = 11 % 5
1
```


###  Native numeric types

Python offers natively four main native numeric type, `bool`, `integer`,
`float` and `complex`. But always keep in mind that they are the poor's man
version of their mathematical equivalent (Boolean ($\mathbb{B}$), Integer
($\mathbb{Z}$), Real ($\mathbb{R}$) and Complex ($\mathbb{C}$)). `ìnteger` have
limited range, `float` and `complex` have limited range and precision.

In the case of `float` and `complex`, this has very important consequences.

``` python
>>> 0.3 == 0.1*3
False
>>> 0.5 == 0.1*5
True
```

The reason is that the decimal number `0.1` cannot be represented exactly is only
approximated[^1]. On most machines, if Python were to print the true decimal value of the binary approximation stored for 0.1, it would have to display

``` python
>>> 0.1
0.1000000000000000055511151231257827021181583404541015625
```

Not very convenient... Consequently, Python (as many other languages) chose to
display a rounded value instead. If you want to know more, have a look at the
[Floating Point Arithmetic: Issues and Limitations](https://docs.python.org/3/tutorial/floatingpoint.html)
chapter in the official
[Python 3 tutorial](https://docs.python.org/3/tutorial/index.html). An
immediate and practical consequence is that what you see in the console is not
always what you get in memory, even if they're reasonably close.

[^1]: *What Every Computer Scientist Should Know About Floating-Point Arithmetic*  
      David Goldberg, Computing Surveys, 1991.


For each type, there exist many ways to specify the same number.

``` python
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

But you can also force the type of any quantity by casting it.

``` python
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
numbers and the
[complex mathematical module](https://docs.python.org/3/library/cmath.html) for
complex numbers.

**Power and logarithmic functions** 

``` python
>>> from math import *
>>> log(exp(1.234))
1.234
```

**Trigonometric functions**

``` python
>>> from math import *
>>> asin(sin(1.234))
1.234
```

**Hyperbolic functions**

``` python
>>> from math import *
>>> asinh(sinh(1.234))
1.234
```

**Special functions**

``` python
>>> from math import *
>>> gamma(2.0)
1.0
```

**Constants**

``` python
>>> from math import *
>>> pi
3.141592653589793
>>> e
2.718281828459045
>>> nan
nan
>>> inf
inf
```


### Logical operations

Logic is an important part of Python because this allows to manipulate and
compare quantities, including numbers, and we'll see later that it works for
all kind of objects.

``` python
>>> True and True # Logical and
>>> 42 or 57      # Logical or
>>> 1 == 2-1      # Equality test
>>> 1 != 2        # Inequality test
>>> 1 is 2-1      # Identity test
>>> not 24        # Negation
```

Note that the `is` keyword really means identity, it is not a test for equality.

``` python
>>> 1 is 1.0
False
>>> True is 1
False
>>> True and 1
True
```

### Bitwise operations

Bitwise operations are logical operations that operate a the bit level. They
might be useful in some situations but we won't use them in this course.

``` python
>>> 1 | 2   # bitwise or
>>> 1 & 2   # bitwise and
>>> 1 ^ 2   # bitwise xor
>>> 8 << 2  # bitwise left shift
>>> 8 >> 2  # bitwise right shift
>>> ~8	  # bitwise negation
```




Python is much more
-------------------------------------------------------------------------------

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



Running scripts
-------------------------------------------------------------------------------

Until now, we have been mostly typing some Python expressions directly into
the interpreter, meaning we had to type and retype the same expression again
and again. To save us some time, it's time to put all these commands into a
file that will be ran by the Python interpreter. First, chose a text editor you
might like and fill it with some python commands.

``` python
print("Hello world!")
```

Then save it with the name `script.py`. The `.py` is the regular file extension
used for Python programs. You are free to use any exension you like, but using
`.py` is a damn good idea since the operating system can make the connection
with Python based on this extension.

To run this script, we have two options. First, we can start it using the
regular python interpreter.

``` bash
$ python script.py
Hello world!
$
```

If you run the above command, Python will terminate as soon as your program
has ended. If you want to stay within the Python interpreter, you'll have to use
the `-i` switch (interactive mode) that tells Python to not exit once the program
has finished.

``` bash
$ python script.py
Hello world!
>>> 
```

Another option is to use [IPython] that allows to run a script from the within
the interpreter.

``` python
[1]: %run script.py
Hello world!
[2]: 
```

### Indentation

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



The Jupyter notebook
-------------------------------------------------------------------------------

The [Jupyter] notebook is a web application that allows you to create and share
documents that contain live code, equations, visualizations and explanatory
text. Uses include (but not limited to):

 * data cleaning and transformation
 * numerical simulation
 * statistical modeling
 * machine learning

The Jupyter notebook is not restricted to python and support for over 40
programming languages, including those popular in Data Science such as Python,
R, Julia and Scala.

You can try it [online](https://try.jupyter.org) but you can also start a new
one locally:

```shell
$ jupyter notebook
```

This should open a new tab in your browser (or open a new browser if it was
closed) showing your available notebooks. There should be none, so you can
create a new one and start typing python code.

We won't explore all that you can do with notebook during this course but you can
have a look at the [nbviewer](http://nbviewer.jupyter.org) to see what can be
done with them.



Exercises
-------------------------------------------------------------------------------

We'll stop here with this very short introduction to Python. It's now time to
move on to programming with python. So now, shutdown your computer, grab a pen
a sheet of paper and try to answer these exercices without typing them in a
Python interpreter. Once you've answered every questiosn, you can chek them.

###Find the type of the following expressions

``` python
.0
```

``` python
-1
```

``` python
1,
```

``` python
'4.0 + 5.0'
```

``` python
1e2
```

``` python
1j
```

``` python
[{()}]
```

``` python
float('nan')
```


### Are these legal python expressions?

```python
1 + 1 == 2
```

```python
1 = 2
```

``` python
(1,)[0] 
```

``` python
1 + 1i
```

``` python
1 <- 2
```

``` python
0.+.0
```

``` python
3***3
```

``` python
3 <<2>> 3
```

``` python
[({})]
```


### Find the result of the following expressions

``` python
1.+1,
```

``` python
1,+1.
```

``` python
(1,)*3
```

``` python
1e1000 - 1e1000
```

``` python
'abc'*3
```

``` python
3 or 10
```

``` python
3 <2> 3
```

### How to...

* Build the empty set?
* Get the list of unique letters composing "abracadabra"
* Build a tuple of two empty lists
* Generate a list of all even numbers between 20 and 40 (included)
* Check if a word is a palindrom?
* Transform the string "1.2" into a float?
* Count the number of unique elements in a list?
* Find the maximum representable integer ?
* Print the string `"Isn't, he said"` (including quotes)?
* Swap the content of two variables?



Resources
-------------------------------------------------------------------------------

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
  
* [**Programming with Python**](https://github.com/vsego/python-lecture-notes) are
  the lecture notes from the course taught at the University of Manchester in
  the academic year 2014/15. The aim of the course is to lay a strong
  foundation for your future programming requirements, be they in Python or
  some other language or a similar tool.  

* [**Scipy Lecture Notes**](http://www.scipy-lectures.org) are a set of tutorials
  on the scientific Python ecosystem: a quick introduction to central tools and
  techniques. The different chapters each correspond to a 1 to 2 hours course
  with increasing level of expertise, from beginner to expert.


<!----------------------------- External links ------------------------------->
[Anaconda]:   https://www.anaconda.com
[Canopy]:     https://enthought.com/products/canopy/
[Python]:     http://www.python.org
[Numpy]:      http://www.numpy.org
[Scipy]:      http://www.scipy.org
[Pandas]:     http://pandas.pydata.org
[Matplotlib]: http://matplotlib.org
[IPython]:    http://ipython.org
[Jupyter]:    http://jupyter.org
[Git]:        https://git-scm.com
[OpenGL]:     https://www.opengl.org
[Glumpy]:     https://glumpy.github.io
[Bokeh]:      https://bokeh.org
[Cython]:     http://cython.org
[EDMI]:       http://www.math.u-bordeaux1.fr/ED/ecole_doctorale/
[University of Bordeaux]: http://www.u-bordeaux.com
[Unicode]:    https://en.wikipedia.org/wiki/Unicode
<!---------------------------------------------------------------------------->
