---
layout: default
---
# Part 4: Imports and packages

### Imports

One of the powerful aspects of Python (and most other programming languages) is the ability to utilise external libraries and packages to extend the base functionality of Python

It is best-practice to keep all your imports at the top of your file or Notebook.

You can either import a package or library directly:

`import sklearn`

or import a particular subpackage, function or object from a library:

`from sklearn import datasets`

You can also provide an alias for an imported package using the `import ... as ...` syntax:

`import numpy as np`

Once a package has been imported, you can access the methods and objects from that package from the package name:

`np.mean([1,2,3,4])`


```python
import pandas

print(pandas.__version__)
```

>    0.23.4


You can also import functions and code from python files (ending in `.py`) in your local directory.

In this example, I have created a file called `random_numbers.py`, and placed it in the same folder as my Jupyter Notebook.

The contents of this file are:

```
import random

def print_random_number():
    '''Prints a random number between 0 and 1'''
    return random.random()
```

We can import the function `print_random_number` from this file:


```python
from random_numbers import print_random_number

print_random_number()
```




>    0.9319659068831242



You can also import Python code from other directories, however in the interests of time we won't discuss that further. If you are interested in how to structure a Python project or package, [this](https://docs.python.org/3/tutorial/modules.html#packages) is a good place to start.

### Useful packages

While this list is by no means exhaustive, here are some of the key packages that you should be familiar with (i.e. they will make your life easier!):

- [PANDAS](https://pandas.pydata.org/): Python data analysis library. Built on top of NumPy.
- [NumPy](https://numpy.org/): Numerical Python library. Matrices, fast data processing, efficient subsetting of data arrays. Invaluable for any serious data work.
- [SciPy](https://scipy.org/scipylib/): Routines for numerical integration, interpolation, optimization, linear algebra and statistics.
- [Matplotlib](https://matplotlib.org/): Plotting. More plotting. So many beautiful plots.
- [Seaborn](https://seaborn.pydata.org/): Statistical data visualisation. Beautiful plots with minimal work. Built on top of Matplotlib.
- [BioPython](https://biopython.org/): A set of tools for dealing with biological data and databases.
- [Scikit-Learn](https://scikit-learn.org/stable/): Tools for data mining, data analysis and machine learning.
- [StatsModels](https://www.statsmodels.org): Statistical tests and data exploration.

[**&#8592; Previous Lesson: Functions, Loops and Conditionals**](https://andrewguy.github.io/training/workshops/Intro_to_Python/lessons/03_functions-loops-and-conditionals)

[**Next Lesson: Data Manipulation and Plotting &#8594;**](https://andrewguy.github.io/training/workshops/Intro_to_Python/lessons/05_data-manipulation-and-plotting)