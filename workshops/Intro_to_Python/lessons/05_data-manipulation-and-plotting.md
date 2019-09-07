---
layout: default
---
# Part 5: Data manipulation and plotting

## Data exploration with `pandas` and `matplotlib`

Now that we've covered some of the basics of the Python language, we can explore some basic data analysis using the `pandas` and `matplotlib` Python libraries.

If you are using Jupyter Lab through CloudStor or Binder, you should already have the required packages installed.

If you get an error when you try to import the following libraries, you will have to install the relevant package with either `pip` or `conda` package managers (depending on how you have installed Python).

This is as simple as running `pip install seaborn` or `conda install seaborn` in your terminal.




### Import relevant librarires

We begin by importing all the libraries we are likely to use. Don't worry if you're not sure what you will need later on - you can always import a library when you need it. However, it's good practice to keep your imports at the start of your analysis.


```python
import numpy
import pandas
import seaborn
from scipy import stats
import matplotlib.pyplot as plt
```

### Load and examine data

We will now load a `.csv` data file using pandas. If you don't already have this file in your working directory, download it from [here](https://raw.githubusercontent.com/andrewguy/Training/master/Intro_to_Python/data/proteome_data.csv).

Alternatively, you can run the following bash code in your Jupyter Notebook to automatically download the file into your working directory (the `%%bash` line is a bit of "cell magic" that tells Jupyter Notebook to run that cell as a bash command):

(Note that this might not work if you are running a local Jupyter notebook on Windows.)


```bash
%%bash
wget https://raw.githubusercontent.com/andrewguy/Training/master/workshops/Intro_to_Python/data/proteome_data.csv
```

Loading the data:

```python
gene_data = pandas.read_csv('proteome_data.csv', sep=',')
```

The `gene_data` variable is a Pandas DataFrame:


```python
type(gene_data)
```




>    pandas.core.frame.DataFrame



We can use some of the built in DataFrame functions to examine the data. `head()` shows the first few rows, `describe()` calculates some basic summary statistics, while `info()` gives us detailed information on the columns and types of data in each column.


```python
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
gene_data.describe()
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
      <th>count</th>
      <td>5247.000000</td>
      <td>5247.000000</td>
      <td>5247.000000</td>
      <td>5247.000000</td>
      <td>5247.000000</td>
      <td>5247.000000</td>
      <td>5247.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>22.233842</td>
      <td>14.702384</td>
      <td>3.237848</td>
      <td>1.146499</td>
      <td>778.699638</td>
      <td>-46.702499</td>
      <td>-46.524707</td>
    </tr>
    <tr>
      <th>std</th>
      <td>19.658567</td>
      <td>10.035328</td>
      <td>6.892031</td>
      <td>3.304764</td>
      <td>877.389801</td>
      <td>48.561593</td>
      <td>48.726494</td>
    </tr>
    <tr>
      <th>min</th>
      <td>0.160000</td>
      <td>0.170000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>35.000000</td>
      <td>-99.000000</td>
      <td>-99.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>7.180000</td>
      <td>7.555000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>275.000000</td>
      <td>-99.000000</td>
      <td>-99.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>15.920000</td>
      <td>12.610000</td>
      <td>0.000000</td>
      <td>0.220000</td>
      <td>477.000000</td>
      <td>-2.380000</td>
      <td>-2.060000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>32.195000</td>
      <td>19.170000</td>
      <td>4.140000</td>
      <td>0.770000</td>
      <td>956.000000</td>
      <td>-1.780000</td>
      <td>-1.440000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>100.000000</td>
      <td>91.190000</td>
      <td>100.000000</td>
      <td>28.160000</td>
      <td>10287.000000</td>
      <td>2.690000</td>
      <td>2.590000</td>
    </tr>
  </tbody>
</table>
</div>




```python
gene_data.info()
```

>    <class 'pandas.core.frame.DataFrame'>  
>    RangeIndex: 5247 entries, 0 to 5246  
>    Data columns (total 8 columns):  
>    Protein ID                5247 non-null object  
>    Disorder                  5247 non-null float64  
>    Linear B-cell Epitopes    5247 non-null float64  
>    Tandem Repeats            5247 non-null float64  
>    Non-syn SNPs              5247 non-null float64  
>    Protein Length            5247 non-null int64  
>    Tajimas D (Guinea)        5247 non-null float64  
>    Tajimas D (Gambia)        5247 non-null float64  
>    dtypes: float64(6), int64(1), object(1)  
>    memory usage: 328.0+ KB  


To access data from a particular column, we can use square brackets `[]`, putting the column name within the brackets (like accessing a dictionary item):


```python
# Get data for a particular column
gene_data['Disorder']
```

(The data output is rather large, so we are not showing it here)


However, if your column names are valid Python variable names, you can access columns using the `.` syntax:

(Note that we don't need to enclose the column name in quotes, unlike when accessing using `[]`.


```python
gene_data.Disorder
```






We could also use an external library (such as `scipy.stats`) to get some basic summary statistics for a column. Note that `stats` was imported from `scipy` earlier.


```python
stats.describe(gene_data['Disorder'])
```




>    DescribeResult(nobs=5247, minmax=(0.16, 100.0), mean=22.23384219554031, variance=386.4592723868353, skewness=1.2867352707379653, kurtosis=1.3764282593472768)



We can also use the default plotting capabilities in `pandas` to plot a quick histogram of the data:


```python
gene_data.hist(column='Disorder')
```




>    array([[<matplotlib.axes._subplots.AxesSubplot object at 0x7f41ee1adef0>]],  
>          dtype=object)




![png](../img/output_155_1.png)


We might want to add more bins to the histogram - we can do this with the `bins` argument in the `hist` function:


```python
gene_data.hist(column='Disorder', bins=20)
```




>    array([[<matplotlib.axes._subplots.AxesSubplot object at 0x7f41ee061eb8>]],
>          dtype=object)




![png](../img/output_157_1.png)


### Using Matplotlib

While we can use the built in plotting functions in `Pandas`, you will end up needing to use `matplotlib` to build more complicated plots.

There are two main ways of plotting with `matplotlib`, which can be very confusing when trying to combine examples from Google!

In brief, these two interfaces are:
- MATLAB style plotting using pyplot
- Object Oriented Interface

We have decided to demonstrate the Object Oriented Interface here, because we feel that this is ultimately more powerful, and arguably much easier to use when constructing complex mutli-panel figures, or working with several figures at once.

With that out of the way, on to some plotting!



We start by creating a [`Figure`](https://matplotlib.org/api/_as_gen/matplotlib.figure.Figure.html#matplotlib.figure.Figure) object. We need to define a bit of `matplotlib` terminology here.

- `Figure` object: A container for all your individual plots.
- `Axes` object: An individual plot. Can be multiple `axes` on a `Figure`.

If we're considering a mutlipanel figure in a scientific journal, the `Figure` object would be the overall figure, whereas the `Axes` would be each individual panel. Don't confuse the `Axes` object with an axis on a plot (e.g. x-axis). These are different things!

### Creating a scatter plot
The following code creates a figure with a single panel (one `Axes` object). We are going to set the figure size (in inches, not pixels!). Note the use of a `tuple` to specify figure size.

We then create a `scatter` plot on the `Axes` object, setting `x` and `y` values to be Protein Length and level of Disorder respectively:


```python
fig, ax = plt.subplots(figsize=(5, 4))

# Now, using the `ax` object, we draw a scatter plot
ax.scatter(x=gene_data['Protein Length'], y=gene_data['Disorder'])

fig.show()
```


![png](../img/output_160_1.png)


This plot is OK, but could do with some polishing. We can't really see all of the points (maybe a density estimation plot would be better??), and we need some labels...


```python
# Initialise a figure, with a number of subplots. Each subplot is called an axis - this is what we draw our plot on.
fig, ax = plt.subplots(figsize=(5, 4))

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



![png](../img/output_162_1.png)


We still have an issue with the number of data points. To deal with this, we can do a kernel density estimation.

We will use the seaborn library to do this. Seaborn provides some very nice plotting functions, with a very simple interface.


```python
kde_plot = seaborn.jointplot(x="Protein Length", y="Disorder", data=gene_data, kind="kde")
```


![png](../img/output_164_1.png)


We could also show the data as a hex-bin plot:


```python
hex_plot = seaborn.jointplot(x="Protein Length", y="Disorder", data=gene_data, kind="hex")
```


![png](../img/output_166_1.png)


If we want to save the figures for later use, we just call the `savefig` function:


```python
kde_plot.savefig('kde_plot.png')
hex_plot.savefig('hex_plot.png')
```

It's also worth saving files as `.svg`, which is a vector graphics format. This means you can easily make small adjustments in a program such as Adobe Illustrator or Inkscape.


```python
kde_plot.savefig('kde_plot.svg')
hex_plot.savefig('hex_plot.svg')
```

[**Next Lesson: Getting Help**](https://andrewguy.github.io/Training/workshops/Intro_to_Python/lessons/06_getting-help)