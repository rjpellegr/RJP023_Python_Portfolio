# RJP023_Python_Portfolio
A repo of code I learned as part of Louisiana Tech's computational biology (BISC 450C V84) coursework. For use as both a reference and as a submission for my final project for spring quarter 2023.


## Using Jupyter Notebooks

A brief introduction to Jupyter's Python 3 notebooks and its capabilities.

```python
%matplotlib inline 
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
sns.set(style = "darkgrid")
```


```python
df = pd.read_csv('/home/student/Desktop/classroom/myfiles/notebooks/fortune500.csv')
```


```python
df.head()
```


<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Year</th>
      <th>Rank</th>
      <th>Company</th>
      <th>Revenue (in millions)</th>
      <th>Profit (in millions)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>1955</td>
      <td>1</td>
      <td>General Motors</td>
      <td>9823.5</td>
      <td>806</td>
    </tr>
    <tr>
      <td>1</td>
      <td>1955</td>
      <td>2</td>
      <td>Exxon Mobil</td>
      <td>5661.4</td>
      <td>584.8</td>
    </tr>
    <tr>
      <td>2</td>
      <td>1955</td>
      <td>3</td>
      <td>U.S. Steel</td>
      <td>3250.4</td>
      <td>195.4</td>
    </tr>
    <tr>
      <td>3</td>
      <td>1955</td>
      <td>4</td>
      <td>General Electric</td>
      <td>2959.1</td>
      <td>212.6</td>
    </tr>
    <tr>
      <td>4</td>
      <td>1955</td>
      <td>5</td>
      <td>Esmark</td>
      <td>2510.8</td>
      <td>19.1</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.tail()
```


<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Year</th>
      <th>Rank</th>
      <th>Company</th>
      <th>Revenue (in millions)</th>
      <th>Profit (in millions)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>25495</td>
      <td>2005</td>
      <td>496</td>
      <td>Wm. Wrigley Jr.</td>
      <td>3648.6</td>
      <td>493</td>
    </tr>
    <tr>
      <td>25496</td>
      <td>2005</td>
      <td>497</td>
      <td>Peabody Energy</td>
      <td>3631.6</td>
      <td>175.4</td>
    </tr>
    <tr>
      <td>25497</td>
      <td>2005</td>
      <td>498</td>
      <td>Wendy's International</td>
      <td>3630.4</td>
      <td>57.8</td>
    </tr>
    <tr>
      <td>25498</td>
      <td>2005</td>
      <td>499</td>
      <td>Kindred Healthcare</td>
      <td>3616.6</td>
      <td>70.6</td>
    </tr>
    <tr>
      <td>25499</td>
      <td>2005</td>
      <td>500</td>
      <td>Cincinnati Financial</td>
      <td>3614.0</td>
      <td>584</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.columns = ['Year', 'Rank', 'Company', 'Revenue', 'Profit']
```


```python
df.head()
```


<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Year</th>
      <th>Rank</th>
      <th>Company</th>
      <th>Revenue</th>
      <th>Profit</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>1955</td>
      <td>1</td>
      <td>General Motors</td>
      <td>9823.5</td>
      <td>806</td>
    </tr>
    <tr>
      <td>1</td>
      <td>1955</td>
      <td>2</td>
      <td>Exxon Mobil</td>
      <td>5661.4</td>
      <td>584.8</td>
    </tr>
    <tr>
      <td>2</td>
      <td>1955</td>
      <td>3</td>
      <td>U.S. Steel</td>
      <td>3250.4</td>
      <td>195.4</td>
    </tr>
    <tr>
      <td>3</td>
      <td>1955</td>
      <td>4</td>
      <td>General Electric</td>
      <td>2959.1</td>
      <td>212.6</td>
    </tr>
    <tr>
      <td>4</td>
      <td>1955</td>
      <td>5</td>
      <td>Esmark</td>
      <td>2510.8</td>
      <td>19.1</td>
    </tr>
  </tbody>
</table>
</div>




```python
len(df)
```




    25500




```python
df.dtypes
```




    Year         int64
    Rank         int64
    Company     object
    Revenue    float64
    Profit      object
    dtype: object




```python
non_numeric_profits = df.Profit.str.contains('[^0-9.-]')
df.loc[non_numeric_profits].head()
```


<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Year</th>
      <th>Rank</th>
      <th>Company</th>
      <th>Revenue</th>
      <th>Profit</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>228</td>
      <td>1955</td>
      <td>229</td>
      <td>Norton</td>
      <td>135.0</td>
      <td>N.A.</td>
    </tr>
    <tr>
      <td>290</td>
      <td>1955</td>
      <td>291</td>
      <td>Schlitz Brewing</td>
      <td>100.0</td>
      <td>N.A.</td>
    </tr>
    <tr>
      <td>294</td>
      <td>1955</td>
      <td>295</td>
      <td>Pacific Vegetable Oil</td>
      <td>97.9</td>
      <td>N.A.</td>
    </tr>
    <tr>
      <td>296</td>
      <td>1955</td>
      <td>297</td>
      <td>Liebmann Breweries</td>
      <td>96.0</td>
      <td>N.A.</td>
    </tr>
    <tr>
      <td>352</td>
      <td>1955</td>
      <td>353</td>
      <td>Minneapolis-Moline</td>
      <td>77.4</td>
      <td>N.A.</td>
    </tr>
  </tbody>
</table>
</div>




```python
set(df.Profit[non_numeric_profits])
```




    {'N.A.'}




```python
len(df.Profit[non_numeric_profits])
```




    369




```python
bin_sizes, _, _ = plt.hist(df.Year[non_numeric_profits], bins = range(1955, 2005))
```


![output_11_0](https://github.com/rjpellegr/RJP023_Python_Portfolio/assets/134185456/297c979b-b1b1-48ef-8039-936d5942cb32)


```python
df = df.loc[~non_numeric_profits]
df.Profit = df.Profit.apply(pd.to_numeric)
```


```python
len(df)
```




    25131




```python
df.dtypes
```




    Year         int64
    Rank         int64
    Company     object
    Revenue    float64
    Profit     float64
    dtype: object




```python
group_by_year = df.loc[:, ['Year', 'Revenue', 'Profit']].groupby('Year')
avgs = group_by_year.mean()
x = avgs.index
y1 = avgs.Profit
def plot(x, y, ax, title, y_label):
    ax.set_title(title)
    ax.set_ylabel(y_label)
    ax.plot(x, y)
    ax.margins(x = 0, y = 0)
```


```python
fig, ax = plt.subplots()
plot(x, y1, ax, 'Increase in Mean Fortune 500 Company Profits from 1955 to 2005', 'Profit (Millions)')
```


![output_16_0](https://github.com/rjpellegr/RJP023_Python_Portfolio/assets/134185456/53e30bdc-25e4-4f7b-8eb8-3858ed18723e)


```python
y2 = avgs.Revenue
fig, ax = plt.subplots()
plot(x, y2, ax, 'Increase in Mean Fortune 500 Company Revenues from 1955 to 2005', 'Revenue (Millions)')
```


![output_17_0](https://github.com/rjpellegr/RJP023_Python_Portfolio/assets/134185456/2ca9b903-ef98-4588-889d-6e8376e709eb)


```python
def plot_with_std(x, y, stds, ax, title, y_label):
    ax.fill_between(x, y - stds, y + stds, alpha = 0.2)
    plot(x, y, ax, title, y_label)
fig, (ax1, ax2) = plt.subplots(ncols = 2)
title = 'Increase in Mean and std Fortune 500 Company %s from 1955 to 2005'
stds1 = group_by_year.std().Profit.values
stds2 = group_by_year.std().Revenue.values
plot_with_std(x, y1.values, stds1, ax1, title % 'Profits', 'Profit (Millions)')
plot_with_std(x, y2.values, stds2, ax2, title % 'Revenues', 'Revenue (Millions)')
fig.set_size_inches(14, 4)
fig.tight_layout()
```


![output_18_0](https://github.com/rjpellegr/RJP023_Python_Portfolio/assets/134185456/6ae09b4f-9f36-461d-a4b0-7a70bdedb2d9)


## Python Fundamentals

An overview of some basic Python syntax and included functions.

```python
# Any python interpreter can be used as a calculator:
3 + 5 * 4
```




    23




```python
# Save a value to a variable
weight_kg = 60
print(weight_kg)
```

    60



```python
# weight0 = valid
# 0weight = invalid
# Can't start variable name with a number
# Variable names are case sensitive
```


```python
# Three common types of data:
# Integer numbers
# Floating point numbers
# Strings
```


```python
# Floating point number
weight_kg = 60.3
```


```python
# String comprised of letters
patient_name = "Jon Smith"
```


```python
# String comprised of numbers
patient_id = "001"
```


```python
# Use variables in python
weight_lb = 2.2 * weight_kg
print(weight_lb)
```

    132.66



```python
# Concatenate strings
patient_id = "inflam_" + patient_id
print(patient_id)
```

    inflam_001



```python
# Combine print statements
print(patient_id, "weight in kilograms:", weight_kg)
```

    inflam_001 weight in kilograms: 60.3



```python
# Call a function inside another function
print(type(weight_kg))
print(type(patient_id))
```

    <class 'float'>
    <class 'str'>



```python
# Perform calculations inside a print function
print("weight in lbs:", 2.2 * weight_kg)
```

    weight in lbs: 132.66



```python
print(weight_kg)
```

    60.3



```python
weight_kg = 65.0
print("weight in kilograms is now:", weight_kg)
```

    weight in kilograms is now: 65.0


## Analyzing Data
Example analysis of arthritis patient data

### Raw Data
Just basic analysis using numpy


```python
import numpy
```


```python
numpy.loadtxt(fname = "inflammation-01.csv", delimiter = ",")
```




    array([[0., 0., 1., ..., 3., 0., 0.],
           [0., 1., 2., ..., 1., 0., 1.],
           [0., 1., 1., ..., 2., 1., 1.],
           ...,
           [0., 1., 1., ..., 1., 1., 1.],
           [0., 0., 0., ..., 0., 2., 0.],
           [0., 0., 1., ..., 1., 1., 0.]])




```python
data = numpy.loadtxt(fname = "inflammation-01.csv", delimiter = ",")
```


```python
print(data)
```

    [[0. 0. 1. ... 3. 0. 0.]
     [0. 1. 2. ... 1. 0. 1.]
     [0. 1. 1. ... 2. 1. 1.]
     ...
     [0. 1. 1. ... 1. 1. 1.]
     [0. 0. 0. ... 0. 2. 0.]
     [0. 0. 1. ... 1. 1. 0.]]



```python
print(type(data))
```

    <class 'numpy.ndarray'>



```python
print(data.shape)
```

    (60, 40)



```python
print('first value in data:', data[0,0])
```

    first value in data: 0.0



```python
print("middle value in data:", data[29,19])
```

    middle value in data: 16.0



```python
print(data[0:4, 0:10])
```

    [[0. 0. 1. 3. 1. 2. 4. 7. 8. 3.]
     [0. 1. 2. 1. 2. 1. 3. 2. 2. 6.]
     [0. 1. 1. 3. 3. 2. 6. 2. 5. 9.]
     [0. 0. 2. 0. 4. 2. 2. 1. 6. 7.]]



```python
print(data[5:10, 0:10])
```

    [[0. 0. 1. 2. 2. 4. 2. 1. 6. 4.]
     [0. 0. 2. 2. 4. 2. 2. 5. 5. 8.]
     [0. 0. 1. 2. 3. 1. 2. 3. 5. 3.]
     [0. 0. 0. 3. 1. 5. 6. 5. 5. 8.]
     [0. 1. 1. 2. 1. 3. 5. 3. 5. 8.]]



```python
small = data[:3, 36:]
print(small)
```

    [[2. 3. 0. 0.]
     [1. 1. 0. 1.]
     [2. 2. 1. 1.]]



```python
# Use a numpy function
print(numpy.mean(data))
```

    6.14875



```python
maxval, minval, stdval = numpy.amax(data), numpy.amin(data), numpy.std(data)
```


```python
print(maxval)
print(minval)
print(stdval)
```

    20.0
    0.0
    4.613833197118566



```python
maxval = numpy.amax(data)
minval = numpy.amin(data)
stdval = numpy.std(data)
```


```python
print(maxval)
print(minval)
print(stdval)
```

    20.0
    0.0
    4.613833197118566



```python
print("maximum inflammation:", maxval)
print("minimum inflammation:", minval)
print("standard deviation:", stdval)
```

    maximum inflammation: 20.0
    minimum inflammation: 0.0
    standard deviation: 4.613833197118566



```python
# Looking at variation in statistic values i.e. maximum inflammation per patient, average from day one
patient_0 = data[0, :] # 0 on the first axis (rows) everything on the second (columns)
print("maximum inflammation for patient 0:", numpy.amax(patient_0))
```

    maximum inflammation for patient 0: 18.0



```python
print("maximum inflammation for patient 2:", numpy.amax(data[2, :]))
```

    maximum inflammation for patient 2: 19.0



```python
# Average inflammation for each patient (columns)
print(numpy.mean(data, axis = 0))
```

    [ 0.          0.45        1.11666667  1.75        2.43333333  3.15
      3.8         3.88333333  5.23333333  5.51666667  5.95        5.9
      8.35        7.73333333  8.36666667  9.5         9.58333333 10.63333333
     11.56666667 12.35       13.25       11.96666667 11.03333333 10.16666667
     10.          8.66666667  9.15        7.25        7.33333333  6.58333333
      6.06666667  5.95        5.11666667  3.6         3.3         3.56666667
      2.48333333  1.5         1.13333333  0.56666667]



```python
print(numpy.mean(data, axis = 0).shape)
```

    (40,)



```python
# Maximum inflammation for each patient (rows)
print(numpy.mean(data, axis = 1))
```

    [5.45  5.425 6.1   5.9   5.55  6.225 5.975 6.65  6.625 6.525 6.775 5.8
     6.225 5.75  5.225 6.3   6.55  5.7   5.85  6.55  5.775 5.825 6.175 6.1
     5.8   6.425 6.05  6.025 6.175 6.55  6.175 6.35  6.725 6.125 7.075 5.725
     5.925 6.15  6.075 5.75  5.975 5.725 6.3   5.9   6.75  5.925 7.225 6.15
     5.95  6.275 5.7   6.1   6.825 5.975 6.725 5.7   6.25  6.4   7.05  5.9  ]


### Data Visualization
Using numpy and matplotlib to visualize the above data set


```python
import numpy
data = numpy.loadtxt(fname = "inflammation-01.csv", delimiter = ",")
```


```python
# Heat map of patient inflammation over time
import matplotlib.pyplot
image = matplotlib.pyplot.imshow(data)
matplotlib.pyplot.show()
```


![output_1_0](https://github.com/rjpellegr/RJP023_Python_Portfolio/assets/134185456/aa1ec7ea-99a2-42ff-9831-960c038708c8)


```python
# Average inflammation over time
ave_inflammation = numpy.mean(data, axis = 0)
ave_plot = matplotlib.pyplot.plot(ave_inflammation)
matplotlib.pyplot.show()
```


![output_2_0](https://github.com/rjpellegr/RJP023_Python_Portfolio/assets/134185456/6d4053c0-f10b-4cee-bf75-b575822c40e0)


```python
# Maximum inflammation over time
max_plot = matplotlib.pyplot.plot(numpy.amax(data, axis = 0))
matplotlib.pyplot.show()
```


![output_3_0](https://github.com/rjpellegr/RJP023_Python_Portfolio/assets/134185456/f9c2fc1c-e096-4723-a2bd-785d78227c45)


```python
# Minimum inflammation over time
min_plot = matplotlib.pyplot.plot(numpy.amin(data, axis = 0))
matplotlib.pyplot.show()
```


![output_4_0](https://github.com/rjpellegr/RJP023_Python_Portfolio/assets/134185456/23a954f9-00e0-4b6d-ba49-1cf706c98c41)


```python
# All three combined in one figure
fig = matplotlib.pyplot.figure(figsize = (10.0, 3.0))

axes1 = fig.add_subplot(1, 3, 1)
axes2 = fig.add_subplot(1, 3, 2)
axes3 = fig.add_subplot(1, 3, 3)

axes1.set_ylabel("Average")
axes1.plot(numpy.mean(data, axis = 0))

axes2.set_ylabel("Max")
axes2.plot(numpy.amax(data, axis = 0))

axes3.set_ylabel("Min")
axes3.plot(numpy.amin(data, axis = 0))

fig.tight_layout()

matplotlib.pyplot.savefig("Inflammation.png")
matplotlib.pyplot.show()
```


![output_5_0](https://github.com/rjpellegr/RJP023_Python_Portfolio/assets/134185456/0b2c3b35-99e7-4e45-92b2-b8ea2f4380e1)


## Storing Values in Lists

## Using Loops

## Using Multiple Files

## Making Choices

## Functions

## Defensive Programming

## Transcribing DNA into RNA

## Transcribing RNA into Protein
