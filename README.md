
# Scientific Python Crash Course

![](data/XKCD.png)

This is the material for a 24 hours course on Scientific Python that is split
in beginner and advanced modules of 3 hours each. Contributions and feedbacks
welcome. Released under a [CC-BY 4.0
International](https://creativecommons.org/licenses/by/4.0/legalcode) license.  

<a href="http://www.labri.fr/perso/nrougier"><img alt="Nicolas P. Rougier" align="right"/></a><br/>


---
<br/>

### [Installation]() <img src="https://img.shields.io/badge/3H-Beginner-B39DDB.svg?style=flat-square" align="right"/>

<img src="data/indent.png" align="left"/>

This lesson aims at providing the student with a clean development environment,
including Python installation and essential packages (using the [Anaconda]
installer), a decent text editor (e.g. [emacs], [vim], [atom], [notepad++]), a
git command line and a shell. We'll also introduces the Python & [IPython]
shells, the [Jupyter] notebook and explains how to run a python
script from the command line or from inside the [IPython] shell.  

**Keywords**: `anaconda`, `shell`, `notebook`, `script`, `git`, `editor`  
**Prerequisites**: None <br/><br/>


### [Python programming]() <img src="https://img.shields.io/badge/3H-Beginner-B39DDB.svg?style=flat-square" align="right"/>

<img src="data/indent.png" align="left"/>

We introduce here the Python language. Only the bare minimum necessary for
getting started with Numpy and Scipy is addressed here. To learn more about
the language, consider going through the excellent tutorial
https://docs.python.org/tutorial. Dedicated books are also available, such as
http://www.diveintopython.net/.  

**Keywords**: `python`, `types`, `control flow`, `function`, `package`  
**Prerequisites**: [Installation]()
<br/><br/>


### [Numerical computing]() <img src="https://img.shields.io/badge/3H-Beginner-B39DDB.svg?style=flat-square" align="right"/>

<img src="data/indent.png" align="left"/>

> This lesson gives an overview of [NumPy], the core tool for performant
> numerical computing with Python and support for large, multi-dimensional
> arrays and matrices, along with a large collection of high-level mathematical
> functions to operate on these arrays.

**Keywords**: `numpy`, `array`, `dtype`, `shape`, `broadcast`  
**Prerequisites**: [Python programming]()
<br/><br/>


### [Data visualization]() <img src="https://img.shields.io/badge/3H-Beginner-B39DDB.svg?style=flat-square" align="right"/>

<img src="data/indent.png" align="left"/>

Matplotlib is probably the single most used Python package for 2D-graphics. It
provides both a very quick way to visualize data from Python and to produce
publication-quality figures in many formats. In this lesson, we are going to
explore matplotlib, covering most common use cases.

**Keywords**: `matplotlib`, `figure`, `plot`, `data`  
**Prerequisites**: [Python programming](), [Numerical computing]()
<br/><br/>


### [Version Control]() <img src="https://img.shields.io/badge/3H-Advanced-EF5350.svg?style=flat-square" align="right"/>

<img src="data/indent.png" align="left"/>

Version control is the lab notebook of the digital world: it’s what
professionals use to keep track of what they’ve done and to collaborate with
other people. Every large software development project relies on it, and most
programmers use it for their small jobs as well. And it isn’t just for
software: books, papers, small data sets, and anything that changes over time
or needs to be shared can and should be stored in a version control system.

**Keywords**: `git`, `github`, `clone`, `commit`, `push`, `fork`  
**Prerequisites**: [Installation]()
<br/><br/>


### [Scientific computing]() <img src="https://img.shields.io/badge/3H-Advanced-EF5350.svg?style=flat-square" align="right"/>

<img src="data/indent.png" align="left"/>

SciPy contains modules for optimization, linear algebra, integration, interpolation, special functions, FFT, signal and image processing, ODE solvers and other tasks common in science and engineering.


**Keywords**: `linear algebra`, `signal processing`, `analysis`, `integration`, `solvers`  
**Prerequisites**: [Numerical Computing]()
<br/><br/>


### `07` Acceleration <img src="https://img.shields.io/badge/3H-Advanced-EF5350.svg?style=flat-square" align="right"/>

> Numba & Cython can speed up your computation with little efforts. We'll review
> most common techniques.

**Keywords**: `Cython`, `Numba`, `Compiler`, `JIT`

### `08` Vectorization <img src="https://img.shields.io/badge/3H-Advanced-EF5350.svg?style=flat-square" align="right"/>

> The goal of this lesson is to explain some vectorization techniques that
> can drastically improve computation, with several orders of magnitude in
> some cases.

**Keywords**: `Code`, `Problem`, `Spatial`, `Temporal`  

---

This course has been written in March 2019 using  
<img src="https://img.shields.io/badge/OSX-10.14.3-999999.svg?style=flat-square"/> <img src="https://img.shields.io/badge/Python-3.7.2-999999.svg?style=flat-square"/> <img src="https://img.shields.io/badge/Numpy-1.15.2-999999.svg?style=flat-square"/> <img src="https://img.shields.io/badge/Scipy-1.1.0-999999.svg?style=flat-square"/> <img src="https://img.shields.io/badge/Matplotlib-3.0.0-999999.svg?style=flat-square"/> <img src="https://img.shields.io/badge/Cython-0.28.2-999999.svg?style=flat-square"/> <img src="https://img.shields.io/badge/Numba-0.40.0-999999.svg?style=flat-square"/>

Copyright © 2019 [Nicolas P. Rougier](http://www.labri.fr/perso/nrougier)   
Released under a [CC-BY 4.0 International](https://creativecommons.org/licenses/by/4.0/legalcode) license.  
Banner image copyright © Randall Monroe ([XCDD #353](https://xkcd.com/353/))  



[Anaconda]:  https://www.anaconda.com/
[Emacs]:     http://www.emacs.org/
[vim]:       https://www.vim.org/
[Atom]:      https://atom.io/
[Notepad++]: https://notepad-plus-plus.org/
[NumPy]:     http://www.numpy.org/
[IPython]:   http://www.ipython.org/
[Jupyter]:   http://www.jupyter.org/
