
# An Introduction to Python

> Python is an interpreted, high-level, general-purpose programming language. *--Wikipedia*

- No need to compile code before running it (interpreted vs compiled)
- Low-level details such as memory-management are hidden from the user (high-level)
- Can be used for a wide variety of tasks, including web-programming, scientific analysis, server management, file manipulation etc. (general purpose).


In this tutorial we will cover some of the basics of Python, with a focus on usage in a scientific computing setting.

This is not intended to be a comprehensive tutorial, but rather a taste of what is possible with Python, as well as providing a general foundation for you to go and explore Python further.

### Variables, data types


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

### Strings


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

    There are 5268 genes in P. falciparum
    There are 5268 genes in P. falciparum


### Integers


```python
print(number_of_genes)

print(type(number_of_genes))
```

    5601
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




```python
# Booleans

is_protein_coding = True
is_interesting = False

print(is_protein_coding)

```

    True



```python
# Can perform logical tests

# Logical AND

print(is_protein_coding & is_interesting)

# Logical OR

print(is_protein_coding | is_interesting)
```

    False
    True


### Lists


```python
gene_list = ['PF3D7_0731500', 'PF3D7_1133400', "PF3D7_0707300"]

print(gene_list)
```

    ['PF3D7_0731500', 'PF3D7_1133400', 'PF3D7_0707300']



```python
# Check how many elements are in a list

len(gene_list)
```




    3




```python
# Lists can contain any type of data - can also contain mixed data types

complex_list = [1, "A string", [1,2,3], False]

print(complex_list)

print(len(complex_list))
```

    [1, 'A string', [1, 2, 3], False]
    4



```python
# Getting items from a list - zero indexed!

first_gene = gene_list[0]

print(f"First item in list is {first_gene}, and is accessed with index 0")

second_gene = gene_list[1]

print(f"Second item in list is {second_gene}, and is accessed with index 1")

# Can get the last item with index -1 (regardless of list length)

print(f"Last item in list is {gene_list[-1]}, and is accessed with index -1")
```

    First item in list is PF3D7_0731500, and is accessed with index 0
    Second item in list is PF3D7_1133400, and is accessed with index 1
    Last item in list is PF3D7_0707300, and is accessed with index -1



```python
# Can add items to a list

gene_list.append("PF3D7_0712300")

print(gene_list)
```

    ['PF3D7_0731500', 'PF3D7_1133400', 'PF3D7_0707300', 'PF3D7_0712300']



```python
# Can re-assign items in a list

gene_list[0] = "A new gene!"

print(gene_list)
```

    ['A new gene!', 'PF3D7_1133400', 'PF3D7_0707300', 'PF3D7_0712300']


### Dictionaries

Lists are useful when you want to store data and access by index.

However, when you want to assign a unique key to each piece of data, you can use a **dictionary**.

Dictionaries store **key: value** pairs.

Python dictionaries must have a unique key for each entry - corresponding values do not have to be unique.


```python
# Unique gene names allow us to store protein length information in a dictionary

protein_length_dict = {'PF3D7_0731500': 1504, 
                       'PF3D7_1133400': 2056,
                       'PF3D7_0707300': 746}
```


```python
# Access dictionary items with keys

protein_length_dict['PF3D7_0731500']
```




    1504




```python
# Assign new values (or overwrite old ones)

protein_length_dict['new_gene_1'] = 452
```


```python
# Trying to access a key that is not in the dictionary raises an error

protein_length_dict['new_gene_2']
```


    ---------------------------------------------------------------------------

    KeyError                                  Traceback (most recent call last)

    <ipython-input-65-b282ecbde2c4> in <module>
          1 # Trying to access a key that is not the dictionary raises an error
          2 
    ----> 3 protein_length_dict['new_gene_2']
    

    KeyError: 'new_gene_2'



```python
# Can check if a key is in a dictionary

'new_gene_1' in protein_length_dict
```




    True




```python
# Can also get values from dict using get()

protein_length_dict.get("new_gene_1")
```




    452




```python
# get() takes an optional argument that allows us to assign a default value if key is not found.

protein_length_dict.get("new_gene_2", -1)
```




    -1



### Other data types - tuples, sets


```python
# Tuples are like lists, but are immutable (can't be altered once initialised)

header_tuple = ("Gene", "Organism", "data_file", "number_of_counts")

print(header_tuple)
```

    ('Gene', 'Organism', 'data_file', 'number_of_counts')



```python
# Trying to change part of a tuple will raise an exception

header_tuple[1] = "Species"
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-74-6c9b9ba3d674> in <module>
          1 # Trying to change part of a tuple will raise an exception
          2 
    ----> 3 header_tuple[1] = "Species"
    

    TypeError: 'tuple' object does not support item assignment



```python
# Sets are collections of unique objects - support intersection, union etc

gene_ontology_term_set = {"ATP Binding", "GTPase Activity", "Unfolded Protein Binding"}

terms_of_interest = {"ATP Binding", "Enzyme Activity", "Unfolded Protein Binding"}

gene_ontology_term_set.intersection(terms_of_interest)
```




    {'ATP Binding', 'Unfolded Protein Binding'}




```python
# Can create a set from a list containing duplicates - will remove duplicates
# Notice that sets are unordered!

set([1, 2, 3, 1, 2, 5, 3, 6, 5, 3])
```




    {1, 2, 3, 5, 6}



## Functions

Python functions allow us to wrap commonly used pieces of code into reusable methods.

We have already used several built-in functions, including `print()` and `len()`.

Python functions definitions are indicated by the `def` keyword. Past the initial `def` line, all function code is indented by 4 spaces (some editors will convert a tab keystroke to 4 spaces for you). This indentation indicates that this code all belongs to the function.


```python
def get_sum_of_protein_lengths(protein_lengths):
    '''Takes a dictionary of protein lengths and returns the total combined length.
    
    Args:
        protein_lengths (dict): A dictionary mapping gene names to protein lengths.
    Returns:
        int: Combined length of all proteins.
    '''
    lengths = protein_lengths.values()
    summed_lengths = sum(lengths)
    return summed_lengths
```


```python
# Functions are called using ( ) brackets, with arguments provided within the brackets as required.

get_sum_of_protein_lengths(protein_length_dict)
```




    4758



Note the extensive description in the above example (surrounded by triple-quotes)!

This is known as a doc-string (documentation string), and is an excellent way to document your code. Any function without a docstring is effectively useless!

Functions can return values (which are often assigned to a variable), but sometimes they don't return anything at all! Either way, it is good practice to conclude your function with a `return` statement. If you are not returning a value, you can just write `return` or `return None`.


```python
def print_gene_summary(gene_list):
    '''Print a formatted summary of all genes (number of genes in list and number of unique genes)
    
    Args:
        gene_list (list): A list of genes.
    Returns:
        None
    '''
    print(f"There are a total of {len(gene_list)} genes, with {len(set(gene_list))} unique genes.")
    return 
```


```python
gene_list = ['PF3D7_0731500', 'PF3D7_1133400', 'PF3D7_0707300', 'PF3D7_0712300', 'PF3D7_0712300']
print_gene_summary(gene_list)
```

    There are a total of 5 genes, with 4 unique genes.



```python
# While the above function does something, it doesn't return anything we can save into a variable...

function_output = print_gene_summary(gene_list)
```

    There are a total of 5 genes, with 4 unique genes.



```python
print(function_output)
```

    None


## Loops and iterators

We often need to loop through items. We can achieve this with a `for` loop:


```python
for index in [1, 2, 3, 4, 5]:
    print(index)
```

    1
    2
    3
    4
    5



```python
for gene in gene_list:
    print(gene)
```

    PF3D7_0731500
    PF3D7_1133400
    PF3D7_0707300
    PF3D7_0712300
    PF3D7_0712300



```python
# The loop variable can be named whatever you like, but it is best to choose a descriptive name
# Don't do this!

for banana in gene_list:
    print(banana)
```

    PF3D7_0731500
    PF3D7_1133400
    PF3D7_0707300
    PF3D7_0712300
    PF3D7_0712300



```python
# Can loop through a certain number of times using the `range` function

for i in range(10):
    print(f"This is iteration #{i}")
```

    This is iteration #0
    This is iteration #1
    This is iteration #2
    This is iteration #3
    This is iteration #4
    This is iteration #5
    This is iteration #6
    This is iteration #7
    This is iteration #8
    This is iteration #9



```python
# If we want to loop until a condition is met, we can use `while`:
i = 10

while i > 1:
    i = i - 1
    print(i)
```

    9
    8
    7
    6
    5
    4
    3
    2
    1


One danger of using a `while` loop is the potential to loop forever!

Recommendation: if you think you need to use a while loop, consider if there is another (better) way of looping. Can you use a `for` loop instead?

## Conditionals

We often want to perform a task only if a given condition is true (or false).

In Python, we do this with an `if` block (with an optional `elif` and `else` blocks):


```python
if True:
    print("We are within the if block")
elif True:
    print("We are within the elif block")
else:
    print("We are within the else block")
```

    We are within the if block



```python
if False:
    print("We are within the if block")
elif True:
    print("We are within the elif block")
else:
    print("We are within the else block")
```

    We are within the elif block



```python

```

### Imports

One of the powerful aspects of Python (and most other programming languages) is the ability to utilise external libraries and packages to extend the base functionality of Python

It is best-practice to keep all your imports at the top of your file or Notebook.

You can either import a package or library directly:

`import sklearn`

or import a particular subpackage, function or object from a library:

`from sklearn import datasets`

You can also provide an alias for an imported package:

`import numpy as np`

Once a package has been imported, you can access the methods and objects from that package from the package name:

`np.mean([1,2,3,4])`


```python

```

# Part 2: Doing something useful...


```python
import numpy
import pandas
from scipy import stats
import matplotlib.pyplot as plt
```


```python
gene_data = pandas.read_csv('proteome_data.csv', sep=',')
```


```python
# Examine the first few rows in the data frame.
gene_data.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Protein ID</th>
      <th>Disorder</th>
      <th>Linear B-cell Epitopes</th>
      <th>Tandem Repeats</th>
      <th>Non-syn SNPs</th>
      <th>Protein Length</th>
      <th>Tajimas D (Guinea)</th>
      <th>Tajimas D (Gambia)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>mal_mito_1</td>
      <td>0.80</td>
      <td>0.40</td>
      <td>0.0</td>
      <td>0.40</td>
      <td>250</td>
      <td>-99.0</td>
      <td>-99.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>mal_mito_2</td>
      <td>1.46</td>
      <td>3.14</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>478</td>
      <td>-99.0</td>
      <td>-99.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>mal_mito_3</td>
      <td>1.33</td>
      <td>2.93</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>376</td>
      <td>-99.0</td>
      <td>-99.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>PF3D7_0100100</td>
      <td>57.61</td>
      <td>35.64</td>
      <td>1.2</td>
      <td>23.99</td>
      <td>2163</td>
      <td>-99.0</td>
      <td>-99.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>PF3D7_0100200</td>
      <td>8.16</td>
      <td>7.55</td>
      <td>0.0</td>
      <td>15.11</td>
      <td>331</td>
      <td>-99.0</td>
      <td>-99.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# See what columns are labelled
gene_data.columns
```




    Index(['Protein ID', 'Disorder', 'Linear B-cell Epitopes', 'Tandem Repeats',
           'Non-syn SNPs', 'Protein Length', 'Tajimas D (Guinea)',
           'Tajimas D (Gambia)'],
          dtype='object')




```python
# Get data for a particular column
gene_data['Disorder']
```




    0        0.80
    1        1.46
    2        1.33
    3       57.61
    4        8.16
    5       32.71
    6        2.69
    7        7.80
    8        2.99
    9        7.85
    10       5.14
    11      12.29
    12       7.44
    13       9.13
    14       4.26
    15       3.25
    16       6.92
    17       5.25
    18      50.51
    19       7.69
    20      55.14
    21      16.19
    22      16.67
    23       5.60
    24      14.54
    25      30.12
    26      36.84
    27       2.53
    28      27.89
    29      27.72
            ...  
    5217     2.97
    5218    25.60
    5219    48.64
    5220    18.21
    5221     2.22
    5222    14.54
    5223     3.24
    5224    77.99
    5225     0.51
    5226    13.41
    5227     6.67
    5228    14.79
    5229     8.64
    5230    11.71
    5231    11.43
    5232     2.87
    5233     6.10
    5234     7.89
    5235     2.94
    5236     6.74
    5237     0.87
    5238     2.82
    5239     2.48
    5240     1.27
    5241     0.73
    5242    31.15
    5243    11.11
    5244     2.33
    5245     8.16
    5246     3.39
    Name: Disorder, Length: 5247, dtype: float64




```python
# Summarise data

stats.describe(gene_data['Disorder'])
```




    DescribeResult(nobs=5247, minmax=(0.16, 100.0), mean=22.23384219554031, variance=386.4592723868353, skewness=1.2867352707379653, kurtosis=1.3764282593472768)




```python
# Plot some data - using built in histogram function in Pandas dataframes

gene_data.hist(column='Disorder')
```




    array([[<matplotlib.axes._subplots.AxesSubplot object at 0x7f080eac2eb8>]],
          dtype=object)




![png](../img/output_77_1.png)


While we can use the built in plotting functions in `Pandas`, you will end up needing to use `matplotlib` to build more complicated plots.


```python
# Initialise a figure, with a number of subplots. Each subplot is called an axis - this is what we draw our plot on.
fig, ax = plt.subplots()

# Now, using the `ax` object, we draw a scatter plot
ax.scatter(x=gene_data['Protein Length'], y=gene_data['Disorder'])

# Show the plot so far...
fig.show()
```


![png](../img/output_79_0.png)


This plot is OK, but could do with some polishing. We can't really see all of the points (maybe a density estimation plot would be better??), and we need some labels...


```python
# Initialise a figure, with a number of subplots. Each subplot is called an axis - this is what we draw our plot on.
fig, ax = plt.subplots()

# Now, using the `ax` object, we draw a scatter plot. Set point size to 3.
# We also add a bit of transparency to each pont (alpha = 0.3)
ax.scatter(x=gene_data['Protein Length'], y=gene_data['Disorder'], s=3, alpha=0.3)

ax.set_ylabel("Percentage Disorder")

ax.set_xlabel("Protein Length")

# Show the plot so far...
fig.show()

# Save the figure...
fig.savefig("disorder_vs_length_scatter.png")
```


![png](../img/output_81_0.png)



```python
# We still have an issue with the number of data points.
# We can try and do a kernel density estimation
# We will use the seaborn library to do this.
# Seaborn provides some very nice plotting functions, with a very simple interface.

import seaborn

kde_plot = seaborn.jointplot(x="Protein Length", y="Disorder", data=gene_data, kind="kde")
```


![png](../img/output_82_0.png)



```python
# We could also show the data as a hexbin plot
hex_plot = seaborn.jointplot(x="Protein Length", y="Disorder", data=gene_data, kind="hex")
```


![png](../img/output_83_0.png)



```python
kde_plot.savefig('kde_plot.png')
hex_plot.savefig('hex_plot.png')

```

# Part 3: Getting help

There are a number of ways to get help or figure out how to do something new:
    
- Google it
- Stackoverflow
- Read the documentation (often surprisingly useful)
- Look at the source code (can be difficult, but sometimes needed)

Generally:

- If you don't know what tools you need, or what packages you need to use: **Google or Stackoverflow**
- If you are having trouble with code not working, an unusual error etc: **Google or Stackoverflow**
- If you want to know details about a specific package or function: **Documentation or source code.** Google or Stackoverflow if this doesn't help.

Being a proficient coder is not about knowing the details of every package, but rather knowing how to search for this information effectively...


```python

```
