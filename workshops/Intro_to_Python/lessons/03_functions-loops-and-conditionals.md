---
layout: default
---
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