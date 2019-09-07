## Part 2: Variables, data types

Python has a number of [fundamental data types](https://docs.python.org/3/library/stdtypes.html#), including numeric types (`int`, `float` and `complex`), sequence types (`list`, `tuple`, `range`), string types (`str`), mapping types (`dict`) and set types (`set`).

While some of these might sound quite foreign at the moment, we will explore some of these data types in the next few steps.

When writing Python code, we often assign variables to a particular value. In Python, this assignment is performed by writing the variable name on the left, followed by the `=` sign and the value to be assigned on the right. For example:


```python
interesting_gene = "PF3D7_0731500"

is_protein_coding = True

is_expressed_in_gametocytes = False

number_of_genes = 5268

average_gene_length = 1034.56

gene_list = ['PF3D7_0731500', 'PF3D7_1133400', "PF3D7_0707300"]

protein_length_dict = {'PF3D7_0731500': 1504, 
                       'PF3D7_1133400': 2056,
                       'PF3D7_0707300': 746}

gene_ontology_term_set = {"ATP Binding", "GTPase Activity", "Unfolded Protein Binding"}

```

In the above example, we have assigned values to a number of variables.

If we want to find out what value a particular variable point to, we can use the `print` function:


```python
print(number_of_genes)
```

    5268


Alternatively, if you write out the variable name by itself at the end of a code cell in Jupyter Notebook, it will print out the value (just like using the print function):


```python
number_of_genes = 5000

average_gene_length = 1034.56

number_of_genes
```




    5000



If you want to print out mutliple values within a code cell, you will have to use the `print` function.

Any written code often needs comments to explain particular decisions, or alert other contributors to particular issues or design considerations.

In Python, any line that starts with a `#` symbol is considered to be a comment, and is ignored when running the code. For example:


```python
# This is a comment. I can write what I like here...

average_gene_length = 1078.2

# average_gene_length = 9000!  
# Note that the above line is not run, even if it is valid code (except for the # symbol)

print(average_gene_length)
```

    1078.2


While it is good to thoroughly document your code, comments are no replacement for sensible variable names. `average_gene_length` is a much more descriptive variable name than `av_gl` or `x`.

On the topic of variable names, there are a few rules when naming variables:
- Must begin with a letter (a - z, A - B) or underscore (_)
- Other characters can be letters, numbers or _
- Case Sensitive.
- Can be any (reasonable) length.
- There are some reserved words which you cannot use as a variable name because Python uses them for other things.

Apart from this, there are a [few conventions](https://www.python.org/dev/peps/pep-0008/#naming-conventions) for naming particular types of variables. We will use these conventions for the rest of the tutorial, but won't go into more detail here.

## Data types

We will now explore a number of data types in Python.

If you are ever unsure what type a particular variable holds, you can use the `type` function:


```python
type(average_gene_length)
```




    float



### Strings

Strings are a fundamental data type in Python, and hold a string of characters (letters, numbers, symbols... Any unicode character is acceptable!).

There are a number of [built-in functions](https://docs.python.org/3.7/library/stdtypes.html#string-methods) that help us manipulate strings &mdash; we will explore a few of theme here.


```python
# Strings

print(interesting_gene)
print(type(interesting_gene))
```

    PF3D7_0731500
    <class 'str'>



```python
# Can join strings together

file_name = interesting_gene + ".fasta"

file_name
```




    'PF3D7_0731500.fasta'




```python
# Can split strings at particular characters

file_name.split('.')
```




    ['PF3D7_0731500', 'fasta']




```python
# Can check if a string starts/ends with a particular phrase

print(file_name.endswith('.fasta'))

print(file_name.startswith('PV'))
```

    True
    False



```python
# Mutiline strings are also possible - use triple-quotes

multiple_line_string = """This is a
multi-line
string"""

print(multiple_line_string)
```

    This is a
    multi-line
    string



```python
# Many ways to put variables into a string. The easiest way is f-strings
# (not supported on Python versions < 3.6)...

print(f"There are {number_of_genes} genes in P. falciparum")

# Can also use .format()

print("There are {x} genes in P. falciparum".format(x=number_of_genes))
```

    There are 5000 genes in P. falciparum
    There are 5000 genes in P. falciparum


### Integers

Integers (`int`) are one of the several numeric data types, and are used to represent whole numbers.


```python
print(number_of_genes)

print(type(number_of_genes))
```

    5000
    <class 'int'>



```python
# Can add or subtract integers

number_of_genes = 5601

protein_coding = 5014

non_protein_coding_genes = number_of_genes - protein_coding

print(non_protein_coding_genes)
```

    587



```python
# Can divide, multiply, exponentiate

print(786 * 12)

print(20 / 4)

print(20 ** 4)

```

    9432
    5.0
    160000


What do you notice about integer division?


```python
# Hint...
print(type(20 * 4))
print(type(20 / 4))
```

    <class 'int'>
    <class 'float'>


### Floats

Floats (`float`) are another numeric data type used to hold [floating-point numbers](https://en.wikipedia.org/wiki/Floating-point_arithmetic#Floating-point_numbers).

For the moment, you can consider that these are *almost* the same as decimal numbers, with some limitations on precision. See [here](https://docs.python.org/3/tutorial/floatingpoint.html) for an in-depth description of some limitations of floating point numbers.


```python
average_gene_length = 1034.56

type(average_gene_length)
```




    float




```python
# Mixing floats and ints

1034.56 + 34
```




    1068.56



### Booleans

Booleans are a data type that represent True and False, and are often the result of comparing variables (see logical tests below).

There are only two boolean values - `True` and `False`. Capitalisation matters here - `false`, `FALSE`, or `f` are not boolean values!


```python
# Booleans

is_protein_coding = True
is_interesting = False

print(is_protein_coding)

```

    True


### Comparisons

Python has a number of [comparison operators](https://docs.python.org/3/reference/expressions.html#value-comparisons). The operators `<`, `>`, `==`, `>=`, `<=`, and `!=` compare the values of two objects.

All comparison operators will return a boolean value &mdash; either `True` or `False`.


```python
3 < 6
```




    True




```python
3 > 6
```




    False




```python
3 == 6
```




    False




```python
6 == 6
```




    True




```python
6 == '6'
```




    False




```python
6 != '6'
```




    True



### Logical tests

You can also perform logical tests to combine multiple boolean values. These are `and`, `or` and `not`.


```python
# Can perform logical tests


print(f"Is protein coding: {is_protein_coding}")
print(f"Is interesting: {is_interesting}")

# Logical AND
print(f"Is protein coding and interesting: {is_protein_coding and is_interesting}")

# Logical OR
print(f"Is protein coding or interesting: {is_protein_coding or is_interesting}")
```

    Is protein coding: True
    Is interesting: False
    Is protein coding and interesting: False
    Is protein coding or interesting: True



```python
# The `not` test always returns the opposite boolean value.
not True
```




    False



### Lists

Python lists (`list`) are a sequence data type, and can contain any number of values/objects, with no restriction on the type of object at each position in the list.

Lists are initialised with square brackets, with each item in the list separated by a comma:


```python
gene_list = ['PF3D7_0731500', 'PF3D7_1133400', "PF3D7_0707300"]

print(gene_list)
```

    ['PF3D7_0731500', 'PF3D7_1133400', 'PF3D7_0707300']


You can also create a list by calling the list function on another object:


```python
list_of_letters = list('PF3D7_0731500')
print(list_of_letters)
```

    ['P', 'F', '3', 'D', '7', '_', '0', '7', '3', '1', '5', '0', '0']



```python
# Check how many elements are in a list

len(gene_list)
```




    3



Lists can contain any type of data:


```python
# Lists can contain any type of data - can also contain mixed data types

complex_list = [1, "A string", [1,2,3], False]

print(complex_list)

# Note that the length is the length of the outer-most list, regardless of what is in each position.
len(complex_list)
```

    [1, 'A string', [1, 2, 3], False]





    4



Retrieving items from a list is as simple as using square brackets after the list name, with the item index within the brackets.

One very important thing to note here is that Python is a zero-indexed language. That means that the first item in the list is accessed with index `0` (unlike R or Matlab, which are 1-indexed).


```python
# Getting items from a list - zero indexed!

first_gene = gene_list[0]

print(f"Full gene list is {gene_list}")

print(f"First item in list is {first_gene}, and is accessed with index 0")

second_gene = gene_list[1]

print(f"Second item in list is {second_gene}, and is accessed with index 1")

# Can get the last item with index -1 (regardless of list length)

print(f"Last item in list is {gene_list[-1]}, and is accessed with index -1")
```

    Full gene list is ['PF3D7_0731500', 'PF3D7_1133400', 'PF3D7_0707300']
    First item in list is PF3D7_0731500, and is accessed with index 0
    Second item in list is PF3D7_1133400, and is accessed with index 1
    Last item in list is PF3D7_0707300, and is accessed with index -1


You can also perform list slicing to get a subset of items in the list - this always returns another list.

When performing list slicing, you need to specificy the lower bound (inclusive) and the upper bound (not inclusive), seperated by a colon (`:`):


```python
gene_list[0:2]
```




    ['PF3D7_0731500', 'PF3D7_1133400']



Note that we only return the items with index between `0` and `1` in the above example - the upper bound is not inclusive!

You can also return all items to the end of the list (or from the start of the list), by leaving out one of the bounds:


```python
gene_list[:2]
```




    ['PF3D7_0731500', 'PF3D7_1133400']




```python
gene_list[1:]
```




    ['PF3D7_1133400', 'PF3D7_0707300']



Adding items to a list is easy:


```python
# Can add items to a list

gene_list.append("PF3D7_0712300")

print(gene_list)
```

    ['PF3D7_0731500', 'PF3D7_1133400', 'PF3D7_0707300', 'PF3D7_0712300']


Reassigning items in a list is also easy:


```python
# Can re-assign items in a list

gene_list[0] = "A new gene!"

print(gene_list)
```

    ['A new gene!', 'PF3D7_1133400', 'PF3D7_0707300', 'PF3D7_0712300']


### Dictionaries

Lists are useful when you want to store data and access by index.

However, when you want to assign a unique key to each piece of data, you can use a dictionary (`dict`).

Dictionaries store a *mapping* between `key` and `value` pairs.

Python dictionaries must have a unique key for each entry - corresponding values do not have to be unique.

Dictionaries are initialised using curly braces (`{}`), with keys and values separated by a colon (`:`), and each entry separated by a comma (`,`).


```python
# Unique gene names allow us to store protein length information in a dictionary

protein_length_dict = {'PF3D7_0731500': 1504, 
                       'PF3D7_1133400': 2056,
                       'PF3D7_0707300': 746}
```

Values from a dictionary can be accessed in a similar way to list indexing - except you provide the key, rather than the index.

Dictionaries are unordered,so using an index does not make sense (even if you wrote out the dictionary entries in a particular order).


```python
# Access dictionary items with keys

protein_length_dict['PF3D7_0731500']
```




    1504



Similar to lists, assigning a new value to a key is straightforward:


```python
# Assign new values (or overwrite old ones)

protein_length_dict['new_gene_1'] = 452
```

Accessing a key that doesn't exist will raise an error:


```python
protein_length_dict['new_gene_2']
```


    ---------------------------------------------------------------------------

    KeyError                                  Traceback (most recent call last)

    <ipython-input-62-c7a79ee684ff> in <module>()
    ----> 1 protein_length_dict['new_gene_2']
    

    KeyError: 'new_gene_2'


To avoid this, you can check if a key is in a dictionary:


```python
'new_gene_1' in protein_length_dict
```




    True



You can also get values from a dictionary using `get`:


```python
protein_length_dict.get("new_gene_1")
```




    452



`get()` takes an optional argument that allows us to assign a default value if key is not found.


```python
protein_length_dict.get("new_gene_2", -1)
```




    -1



### Other data types - tuples, sets

### Tuples

Tuples (`tuple`) are like lists, but are immutable (can't be altered once initialised). They are initialised like a `list`, but with `()` brackets instead of `[]`.


```python
header_tuple = ("Gene", "Organism", "data_file", "number_of_counts")

print(header_tuple)
```

    ('Gene', 'Organism', 'data_file', 'number_of_counts')


Trying to change part of a tuple will raise an exception


```python
header_tuple[1] = "Species"
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-68-cfb842aca20d> in <module>()
    ----> 1 header_tuple[1] = "Species"
    

    TypeError: 'tuple' object does not support item assignment


### Sets

Sets (`set`) are collections of unique objects &mdash; sets support intersection, union etc


```python
gene_ontology_term_set = {"ATP Binding", "GTPase Activity", "Unfolded Protein Binding"}

terms_of_interest = {"ATP Binding", "Enzyme Activity", "Unfolded Protein Binding"}

gene_ontology_term_set.intersection(terms_of_interest)
```




    {'ATP Binding', 'Unfolded Protein Binding'}



We can create a set from a list containing duplicates &mdash; this will remove duplicates.
Notice that sets are unordered!


```python
set([1, 2, 3, 1, 2, 5, 3, 6, 5, 3])
```




    {1, 2, 3, 5, 6}



## Conclusion, Part 2

That wraps up our overview of basic data types. Take a break and stretch your legs!

There are many other more complex data types from various Python packages. For example, the built-in (`collections` module)[https://docs.python.org/3.7/library/collections.html] has data types such as counters (counts the number of times each value occurs) and ordered dictionaries (like a dictionary, but entries are ordered like a list). Packages such as `numpy` also have their own set of data types.


[**Next Lesson: Variables and data types**](https://andrewguy.github.io/Training/workshops/Intro_to_Python/lessons/03_functions-loops-and-conditionals)