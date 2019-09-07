---
layout: default
---
# Part 3: Functions, loops and conditionals

## Functions

Python functions allow us to wrap commonly used pieces of code into reusable methods.

We have already used several built-in functions, including `print()` and `len()`.

### Defining a function

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

Note the extensive description in the above example (surrounded by triple-quotes)!

This is known as a doc-string (documentation string), and is an excellent way to document your code. Any function without a docstring is effectively useless!

### Calling (or using) a function

Functions are called using `( )` brackets, with arguments provided within the brackets as required.


```python
protein_length_dict = {'PF3D7_0731500': 1504, 
                       'PF3D7_1133400': 2056,
                       'PF3D7_0707300': 746}

get_sum_of_protein_lengths(protein_length_dict)
```




>    4306



### Returning a value from a function

Functions can return values (which are usually assigned to a variable), but sometimes they don't return anything at all!

The returned value is indicated by the `return` statement within the function definition &mdash; the value to be returned is written directly after the `return` statement.

Even if your function is not returning anything, it is good practice to conclude your function with a `return` statement. If you are not returning a value, you can just write `return` or `return None`.

Note that once a function reaches the `return` statement, it does not execute any more code &mdash; `return` essentially tells the function that is has finished running, and needs to return a value!


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


gene_list = ['PF3D7_0731500', 'PF3D7_1133400', 'PF3D7_0707300', 'PF3D7_0712300', 'PF3D7_0712300']
print_gene_summary(gene_list)
```

>    There are a total of 5 genes, with 4 unique genes.


Note that while the above function does something, it doesn't return anything we can save into a variable. If we try and save the output into a variable:


```python
function_output = print_gene_summary(gene_list)
```

>    There are a total of 5 genes, with 4 unique genes.



```python
print(function_output)
```

>    None


### Importing functions from other packages

It is also possible to import functions from other files or packages. This means we don't have to define (`def`) the function within our code, we can just import it and use it. We will discuss imports in more detail later...

## Loops and iterators

When doing programming, we often need to perform the same action on a whole set of objects/data/values.

Programming loops enable us to do this efficiently (without writing out almost identical blocks of code many times).

The main loop used in Python is the `for` loop. (Note that this is a little different to `for` loops in some other languages)

The `for` loop iterates through an iteratable object (i.e. a `list`, `tuple`, `set` etc), letting you run code on each item in the iteratable.

For example, let's iterate over a list of numbers, printing each number in the list:


```python
for index in [1, 2, 3, 4, 5]:
    print(index)
```

>    1  
>    2  
>    3  
>    4  
>    5  


We could also iterate over the list of gene names we created earlier:


```python
for gene in gene_list:
    print(gene)
```

>    PF3D7_0731500  
>    PF3D7_1133400  
>    PF3D7_0707300  
>    PF3D7_0712300  
>    PF3D7_0712300  


Note that the loop variable can be named whatever you like, but it is best to choose a descriptive name.

Don't do this:


```python
for banana in gene_list:
    print(banana)
```

>    PF3D7_0731500  
>    PF3D7_1133400  
>    PF3D7_0707300  
>    PF3D7_0712300  
>    PF3D7_0712300  


A commonly used pattern is to loop a certain number of times using the `range` function:
    
The `range(n)` function returns a sequence of numbers, starting at `0` by default, and returning a total of `n` values.


```python
for i in range(10):
    print(f"This is iteration #{i}")
```

>    This is iteration #0  
>    This is iteration #1  
>    This is iteration #2  
>    This is iteration #3  
>    This is iteration #4  
>    This is iteration #5  
>    This is iteration #6  
>    This is iteration #7  
>    This is iteration #8  
>    This is iteration #9  


Another type of loop is the `while` loop. This allows us to loop until a condition is met:


```python
i = 10

while i > 1:
    i = i - 1
    print(i)
```

>    9  
>    8  
>    7  
>    6  
>    5  
>    4  
>    3  
>    2  
>    1  


One danger of using a `while` loop is the potential to loop forever!

Although `while` loops can be useful in some circumstances, there are often better options. If you think you need to use a while loop, consider if there is another (better) way of looping. Can you use a `for` loop instead?

### A note about indentation

You may note the particular indentation being used in the above examples. In Python, indentation is used to define a block of code. In the above examples, all indented code after the `for` statement is part of the `for` loop. Code that is no longer indented indicates that we have reached the end of the `for` loop. Note that we can also have multiple levels of indentation. What do you think the following code will do?

```
for i in [1, 2, 3]:
    for j in [6, 7, 8]:
        print(i * j)
```

## Conditionals

We often want to perform a task only if a given condition is met.

In Python, we do this with an `if` block (with an optional `elif` and `else` blocks):


```python
read_depth = 561

if read_depth < 10:
    print("We have low read coverage")
elif read_depth < 100:
    print("We have acceptable read coverage")
else:
    print("We have high read coverage")
```

>    We have high read coverage



```python
read_depth = 49

if read_depth < 10:
    print("We have low read coverage")
elif read_depth < 100:
    print("We have acceptable read coverage")
else:
    print("We have high read coverage")
```

>    We have acceptable read coverage


Combined with `for` loops, `if` blocks allow us to create complex rules for processing data.

However, there are often better ways of filtering and processing data using dedicated packages such as `numpy` or `pandas` &mdash; more on this later!


[**Next Lesson: Imports and Packages**](https://andrewguy.github.io/Training/workshops/Intro_to_Python/lessons/04_imports-and-packages)