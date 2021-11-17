
## Installation


This lesson aims at providing the student with a clean development environment,
including Python installation and essential packages (using the [Anaconda]
installer), a decent text editor (e.g. [emacs], [vim], [atom], [notepad++]), a
git command line and a shell. We'll also introduce the Python & [IPython]
shells, the [Jupyter] notebook and explains how to run a python
script from the command line or from inside the [IPython] shell.

<br/>

**Contents**
* [Objectives](#objectives)
* [Installation](#installation) ..............................................................................................................................................
  <img src="https://img.shields.io/badge/-Duration:_30mn-black.svg?style=flat-square" align="right"/>
* [Python, IPython & Jupyter](#python-ipython--jupyter-) ....................................................................................................................
  <img src="https://img.shields.io/badge/-Duration:_15mn-black.svg?style=flat-square" align="right"/>
* [Testing your installation](#testing-your-installation-) .........................................................................................................................
  <img src="https://img.shields.io/badge/-Duration:_15mn-black.svg?style=flat-square" align="right"/>


<br/><br/><br/><br/>

## Objectives

The primary goals of this lesson are:

* To ensure you have a clean Python installation (including [Jupyter])
* To install a decent text editor on your system
* To type a few Python lines and to run a python script
  
### Convention 

During this introduction, we'll use three different kind of console, namely
`shell` (or powershell), `Python` and `IPython`. To help you distinguish them,
there will be a small colored icon in front of them:

<img src="https://img.shields.io/badge/-Shell-black.svg?style=flat-square" align="left"/>

``` bash
GNU bash, version 3.2.57(1)-release-(x86_64-apple-darwin18)
$ _
```

<img src="https://img.shields.io/badge/-Python-blue.svg?style=flat-square" align="left"/>

``` Pycon
Python 3.7.2 (default, Feb 12 2019, 08:15:36)
[Clang 10.0.0 (clang-1000.11.45.5)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> _
```

<img src="https://img.shields.io/badge/-IPython-orange.svg?style=flat-square" align="left"/>

``` IPython
Python 3.7.2 (default, Feb 12 2019, 08:15:36)
Type 'copyright', 'credits' or 'license' for more information
IPython 7.0.1 -- An enhanced Interactive Python. Type '?' for help.

In [1]: _
```

In the examples above, `>>>` is the Python prompt and does not need to be
typed. For IPython, the prompt is more likely to be something like
`[12]:`. There is also a second prompt (`...`) meaning the previous line is not
ended and needs to be terminated. This is for example the case when you enter a
parenthese or an unbalanced expression (e.g. number of opening parenthesis is
greater than the number of closing parenthesis).

If you type a bash command in a Python shell or a Python command in a Bash
shell, the console will report an error.

> **Note**: to exit a Python shell or a regular shell, you can type `exit()` or
type `Control-D`.


<br/><br/>
## Installation <img src="https://img.shields.io/badge/-Duration:_30mn-black.svg?style=flat-square" align="right"/>

As of today (2019), Python exists mainly in two flavors: Python 2.x
(deprecated) and Python 3.x. On some systems, the 2.x version is already
installed and for some systems, the 3.x version might be installed as well (or
instead). However, we cannot use any of them because we'll need to install
several packages that might interfere with the system packages. We'll thus have
to install our own version using [Anaconda] by Continuum Analytics which is a
free Python distribution (including for commercial use and redistribution) and
includes more than 400 of the most popular Python packages for science, math,
engineering, and data analysis.

[Anaconda] is available for several architectures:

* [Anaconda for windows](https://www.anaconda.com/distribution/#windows)
  (Python 3.7 version and the 64-Bit Graphical Installer (614.3 MB))  
* [Anaconda for linux](https://www.anaconda.com/distribution/#linux)
  (Python 3.7 version and the 64-Bit (x86) Installer (652.5 MB)
* [Anaconda for OSX](https://www.anaconda.com/distribution/#macos)
  (Python 3.7 version and the 64-Bit Graphical Installer (652.7 MB))

When asked whether to install Visual Studio, choose yes if you're on Windows.

Once installation has finished, we'll need to test it.  

> **Note** that If you're using a Windows machine, you'll need to install
> [powershell](https://docs.microsoft.com/en-us/powershell/) that let you
> manage your computer from the command line.


You can now open a terminal (or powershell on Windows) and test if you've
access to the `conda` command:

<img src="https://img.shields.io/badge/-Shell-black.svg?style=flat-square" align="left"/>

``` bash
$ conda --version
conda 4.5.12
```

Since the installer might not be up to date (depending on when it was build),
you may need to update your anaconda installation:

<img src="https://img.shields.io/badge/-Shell-black.svg?style=flat-square" align="left"/>

``` bash
$ conda update --all
Collecting package metadata: done
Solving environment: done

## Package Plan ##

...

Proceed ([y]/n)?

...

Preparing transaction: done
Verifying transaction: done
Executing transaction: done

$ conda --version
conda 4.6.4
```

> **Note**: If the `conda` does not work, you'll need to open the Anaconda
> navigator and to update the packages through the interface. The reason why
> the `conda` does not work might be linked to a `PATH` problem. In such case,
> it might be worth to reboot your machine to see if this solves the problem.


### Git, a distributed version control system 

We now need to install Git which is not related to Python and has not been
installed during the previous step. Depending on your system, it might be
already installed but most probably it is not up to date and this is the reason
why we'll install our own version. Download the version for your system and
proceed with installation:

* [Windows](https://git-scm.com/downloads/win)
* [Linux](https://git-scm.com/download/linux)
* [Mac](https://git-scm.com/download/mac)

Once installation has finished, you can type:

<img src="https://img.shields.io/badge/-Shell-black.svg?style=flat-square" align="left"/>

``` bash
$ git --version
2.20.1
```

> **Note**: As for `conda`, this command may not work if your `PATH` has not
> been updated properly. You can try starting a new terminal and/or reboot
> your machine to see if this solves the problem.



### Code editor

The last thing we need to install is a decent code editor. You might have one
already installed on your system and if you're faimilar with it, no need to
install another one. Still, you'll need to configure it properly. If you have
no code editor (or if you're not sure you have one), you need to install
one. There is actually a large choice but I will only list here the most
relevant ones:

* [Atom]
* [Notepad++]
* [Sublime Text]
* [Emacs] (powerful but difficult for a beginner)
* [vim] (powerful but difficult for a beginner)

Whatever the editor you chose, you will need to configure it to **not** use
tabulations but to insert spaces (e.g. 4) when you press the `tab` key. This is
important because if you don't do it and mix spaces and tabulations, Python
will complain (it is not allowed) and using only tabs is generally a bad
idea. The way to configure this is editor dependent so I'll let you search how
to do it in your preferred editor.



<br/><br/>
## Python, IPython & Jupyter <img src="https://img.shields.io/badge/-Duration:_15mn-black.svg?style=flat-square" align="right"/>

You are now ready to start using Python and there are several ways to do that:

1. You can start a Python or IPython shell and type some Python commands
2. You can write a Python script and execute it
3. You can start the Jupyter notebook and type some Python code in the browser  
   (and save your code and results in various formats such as PDF or HTML)

The Python shell can be started using the command `python` or `python3`:

<img src="https://img.shields.io/badge/-Shell-black.svg?style=flat-square" align="left"/>

``` Pycon
$ Python
Python 3.7.2 (default, Feb 12 2019, 08:15:36)
[Clang 10.0.0 (clang-1000.11.45.5)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> _
```

Once inside the sell, you can start typing command:

<img src="https://img.shields.io/badge/-Python-blue.svg?style=flat-square" align="left"/>

``` Pycon
>>> print("Hello world!")
Hello world!
```


The IPython shell can be started using the command `ipython` or `ipython3`:

<img src="https://img.shields.io/badge/-Shell-black.svg?style=flat-square" align="left"/>

``` Pycon
$ IPython
Python 3.7.2 (default, Dec 29 2018, 00:00:04)
Type 'copyright', 'credits' or 'license' for more information
IPython 7.2.0 -- An enhanced Interactive Python. Type '?' for help.

In [1]: _
```

It works pretty much like the default Python shell and you can type commands:

<img src="https://img.shields.io/badge/-IPython-orange.svg?style=flat-square" align="left"/>

``` Pycon
In [1]: print("Hello world!")
Hello world!
```

Both shells allow to enter Python commands, but IPython offers a set of
supplementary commands as well as some goodies such as code completion and
interactive figures. If you don't which one to use, choose IPython (you'll
thank me later).


Using the shell is fine for short code snippets, but as soon as you will want
to write longer program, you'll need first to write your code in a text editor
and then you will execute your code. Let me show you with a very simple script.

Open your text editor and write:

```
print("Hello world!")
```

and save the file as `hello.py`. The `.py` is the regular file extension used
for Python programs. You are free to use any exension you like, but using `.py`
is a good idea since the operating system can identify the file as being a
Python script. 

Take note on where you saved your file because you'll need to go to this place
in the shell in order to be able to run it (you can also use the absolute path
to execute it but it is less convenient.

<img src="https://img.shields.io/badge/-Shell-black.svg?style=flat-square" align="left"/>

``` Bash
# Replace the path with the path where you saved your script
$ cd ~/GitHub/scipy-crash-course/examples 
$ python hello.py
Hello world!
```

If you run the above command, Python will terminate as soon as your program
has ended. If you want to stay within the Python interpreter, you'll have to use
the `-i` switch (interactive mode) that tells Python to not exit once the program
has finished.

The IPython shell allows you to run a script through the magic
command `%run` (there are many [other magic commands](https://ipython.org/ipython-doc/3/interactive/magics.html)).

<img src="https://img.shields.io/badge/-IPython-orange.svg?style=flat-square" align="left"/>

```IPython
In [1]: %run hello.py
Hello world!
```

Last, but not least, you can use the [Jupyter] notebook that is an open-source
web application that allows you to create and share documents that contain live
code, equations, visualizations and narrative text. It's a very powerful tool
and is used by an increasing number of researcher.

![https://blog.jupyter.org/we-analyzed-1-million-jupyter-notebooks-now-you-can-too-guest-post-8116a964b536](data/notebook.png)

If you want to get started with Jupyter notebook, you better read the
[tutorial](https://jupyter.readthedocs.io/en/latest/running.html) at
jupiter.org or this nice
[tutorial](https://www.datacamp.com/community/tutorials/tutorial-jupyter-notebook)
at datacamp.



<br/><br/>
## Testing your installation <img src="https://img.shields.io/badge/-Duration:_15mn-black.svg?style=flat-square" align="right"/>


It's now time to check our installation to see if everything is ok.  At this
point, no need yet to understand what you're typing but we need to check if
some important packages are present with the proper version.


**Checking for numpy**

<img src="https://img.shields.io/badge/-Python-blue.svg?style=flat-square" align="left"/>

``` pycon
>>> import numpy
>>> print(numpy.__version__)
1.15.2
>>> numpy.test() # This can last a few seconds
..........................
```

**Checking for scipy**

<img src="https://img.shields.io/badge/-Python-blue.svg?style=flat-square" align="left"/>

``` pycon
>>> import scipy
>>> print(scipy.__version__)
1.1.0
>>> scipy.test() # This can last several minutes
...........................
```

**Checking for matplotlib**

<img src="https://img.shields.io/badge/-Python-blue.svg?style=flat-square" align="left"/>

``` pycon
>>> import matplotlib
>>> print(matplotlib.__version__)
3.0.0
```

**Checking for cython**

<img src="https://img.shields.io/badge/-Python-blue.svg?style=flat-square" align="left"/>

``` pycon
>>> import cython
>>> print(cython.__version__)
0.28.2
```

**Checking for numba**

<img src="https://img.shields.io/badge/-Python-blue.svg?style=flat-square" align="left"/>

``` pycon
>>> import numba
>>> print(numba.__version__)
0.40.0
>>> numba.test() # This can last several minutes
...........................
```


For each of these packages, the `x.y.z` version should be equal or greater than
the displayed version. If this is not the case, then maybe you conda
installation is not up to date and needs to be upgraded (go back the
[Installation](#installation) section to see how this can be done.


<br/><br/>

##

Copyright © 2019 [Nicolas P. Rougier](http://www.labri.fr/perso/nrougier) •
Released under a [CC-BY 4.0 International](https://creativecommons.org/licenses/by/4.0/legalcode) license.


<!----------------------------- External links ------------------------------->
[Anaconda]:     https://www.anaconda.com
[Python]:       http://www.python.org
[Numpy]:        http://www.numpy.org
[Scipy]:        http://www.scipy.org
[Matplotlib]:   http://matplotlib.org
[IPython]:      http://ipython.org
[Jupyter]:      http://jupyter.org
[Git]:          https://git-scm.com
[Cython]:       http://cython.org
[Unicode]:      https://en.wikipedia.org/wiki/Unicode
[Emacs]:        http://www.emacs.org/
[vim]:          https://www.vim.org/
[Atom]:         https://atom.io/
[Notepad++]:    https://notepad-plus-plus.org/
[Sublime Text]: https://www.sublimetext.com/
<!---------------------------------------------------------------------------->
