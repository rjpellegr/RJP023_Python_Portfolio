# RJP023_Python_Portfolio
A repo of code I learned as part of Louisiana Tech's computational biology (BISC 450C V84) coursework. For use as both a reference and as a submission for my final project for spring quarter 2023.


## Using Jupyter Notebooks

A brief introduction to Jupyter notebooks and its capabilities.

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
Using and manipulating lists/arrays in Python

```python
odds = [1, 3, 5, 7]
print("odds are: ", odds)
```

    odds are:  [1, 3, 5, 7]



```python
print('first element: ', odds[0])
print('last element: ', odds[3])
print('"-1" element: ', odds[-1])
```

    first element:  1
    last element:  7
    "-1" element:  7



```python
names = ['Curie', 'Darwing', 'Turing'] # Typo in Darwin's name
print('names is originally: ', names)
names[1] = 'Darwin' # Correction
print('final value of names: ', names)
```

    names is originally:  ['Curie', 'Darwing', 'Turing']
    final value of names:  ['Curie', 'Darwin', 'Turing']



```python
#name = 'Darwin'
#name[0] = 'd'
```


```python
odds.append(11)
print('odds after adding a value: ', odds)
```

    odds after adding a value:  [1, 3, 5, 7, 11]



```python
removed_element = odds.pop(0)
print('odds after removing first element: ', odds)
print('removed_element: ', removed_element)
```

    odds after removing first element:  [3, 5, 7, 11]
    removed_element:  1



```python
odds.reverse()
print('odds after reversing: ', odds)
```

    odds after reversing:  [11, 7, 5, 3]



```python
odds = [3, 5, 7]
primes = odds
primes.append(2)
print('primes ', primes)
print('odds ', odds)
```

    primes  [3, 5, 7, 2]
    odds  [3, 5, 7, 2]



```python
odds = [3, 5, 7]
primes = list(odds)
primes.append(2)
print('primes: ', primes)
print('odds: ', odds)
```

    primes:  [3, 5, 7, 2]
    odds:  [3, 5, 7]



```python
binomial_name = 'Drosophila melanogaster'
group = binomial_name[0:10]
print('group: ', group)

species = binomial_name[11:23]
print('species: ', species)

chromosomes = ['X', 'Y', '2', '3', '4']
autosomes = chromosomes[2:5]
print('autosomes: ', autosomes)

last = chromosomes[-1]
print('last: ', last)
```

    group:  Drosophila
    species:  melanogaster
    autosomes:  ['2', '3', '4']
    last:  4



```python
date = 'Monday 4 January 2023'
day = date[0:6]
print('Using 0 to begin range: ', day)
day = date[:6]
print('Omitting beginning index: ', day)
```

    Using 0 to begin range:  Monday
    Omitting beginning index:  Monday



```python
months = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec']
sond = months[8:12]
print('With known last position: ', sond)

sond = months[8:len(months)]
print('Using len() to get last entry: ', sond)

sond = months[8:]
print('Omitting ending index: ', sond)
```

    With known last position:  ['Sep', 'Oct', 'Nov', 'Dec']
    Using len() to get last entry:  ['Sep', 'Oct', 'Nov', 'Dec']
    Omitting ending index:  ['Sep', 'Oct', 'Nov', 'Dec']


## Using Loops
Loops and iteration


```python
odds = [1, 3, 5, 7]
```


```python
print(odds[0])
print(odds[1])
print(odds[2])
print(odds[3])
```

    1
    3
    5
    7



```python
#odds = [1, 3, 5]
#print(odds[0])
#print(odds[1])
#print(odds[2])
#print(odds[3])
```


```python
odds = [1, 3, 5, 7, 9, 11, 13, 15, 17, 19]

for num in odds:
    print(num)
```

    1
    3
    5
    7
    9
    11
    13
    15
    17
    19



```python
length = 0
names = ['Curie', 'Darwin', 'Turing']

for value in names:
    length = length + 1
print('There are', length, 'names in the list.')
```

    There are 3 names in the list.



```python
name = 'Rosalind'
for name in ['Curie', 'Darwin', 'Turing']:
    print(name)
print('After the loop, name is', name)
```

    Curie
    Darwin
    Turing
    After the loop, name is Turing



```python
print(len([0, 1, 2, 3]))
```

    4



```python
name = ['Curie', 'Darwin', 'Turing']
print(len(name))
```

    3


## Using Multiple Files
Using multiple files in the Python environment with glob


```python
import glob
```


```python
print(glob.glob('inflammation*.csv'))
```

    ['inflammation-05.csv', 'inflammation-12.csv', 'inflammation-04.csv', 'inflammation-08.csv', 'inflammation-10.csv', 'inflammation-06.csv', 'inflammation-09.csv', 'inflammation-01.csv', 'inflammation-07.csv', 'inflammation-11.csv', 'inflammation-03.csv', 'inflammation-02.csv']



```python
import glob
import numpy
import matplotlib.pyplot

filenames = sorted(glob.glob('inflammation*.csv'))
filenames = filenames[0:3]

for filename in filenames:
    print(filename)
    
    data = numpy.loadtxt(fname=filename, delimiter= ',')
    
    fig = matplotlib.pyplot.figure(figsize = (10.0, 3.0))
    
    axes1 = fig.add_subplot(1,3,1)
    axes2 = fig.add_subplot(1,3,2)
    axes3 = fig.add_subplot(1,3,3)
    
    axes1.set_ylabel('Average')
    axes1.plot(numpy.mean(data, axis = 0))
    
    axes2.set_ylabel('Max')
    axes2.plot(numpy.amax(data, axis = 0))
    
    axes3.set_ylabel('Min')
    axes3.plot(numpy.amin(data, axis = 0))
    
    fig.tight_layout()
    matplotlib.pyplot.show()
```

    inflammation-01.csv


![output_2_1](https://github.com/rjpellegr/RJP023_Python_Portfolio/assets/134185456/84794345-9a71-4b4a-9ad7-2a22372974eb)


    inflammation-02.csv


![output_2_3](https://github.com/rjpellegr/RJP023_Python_Portfolio/assets/134185456/8bfefbcc-cef2-42b8-8a0f-16ca59edac99)


    inflammation-03.csv


![output_2_5](https://github.com/rjpellegr/RJP023_Python_Portfolio/assets/134185456/46ace1c4-e54b-4d37-af4f-3049e9daca27)


## Making Choices
The basics of using conditionals


```python
num = 37
if num > 100:
    print('greater')
else:
    print('not greater')
print('done')
```

    not greater
    done



```python
num = 53
print('before conditional...')
if num > 100:
    print(num, 'is greater than 100')
print('...after conditional')
```

    before conditional...
    ...after conditional



```python
num = 14
if num > 0:
    print(num, 'is positive')
elif num == 0:
    print(num, 'is zero')
else: print(num, 'is negative')
```

    14 is positive



```python
if (1 > 0) and (-1 >= 0):
    print('both parts are true')
else:
    print('at least one part is false')
```

    at least one part is false



```python
if (-1 > 0) or (-1 >= 0):
    print('at least one part is true')
else:
    print('both of these are false')
```

    both of these are false


### Part 2: Using Actual Data
Putting it into practice, using the same inflammation data from previous exercises.


```python
import numpy
```


```python
data = numpy.loadtxt(fname='inflammation-01.csv', delimiter = ',')
```


```python
max_inflammation_0 = numpy.amax(data, axis=0)[0]
```


```python
max_inflammation_20 = numpy.amax(data, axis=0)[20]
```


```python
if max_inflammation_0 == 0 and max_inflammation_20 == 20:
    print('Suspicious looking maxima!')
```

    Suspicious looking maxima!



```python
max_inflammation_20 = numpy.amax(data, axis=0)[20]
if max_inflammation_0 == 0 and max_inflammation_20 == 20:
    print('Suspicious looking maxima!')
elif numpy.sum(numpy.amin(data, axis=0)) == 0:
    print('Minima add up to zero!')
else:
    print('Seems OK!')
```

    Suspicious looking maxima!



```python
data = numpy.loadtxt(fname = 'inflammation-03.csv', delimiter=',')

max_inflammation_0 = numpy.amax(data, axis=0)[0]

max_inflammation_20 = numpy.amax(data, axis=0)[20]

if max_inflammation_0 == 0 and max_inflammation_20 == 20:
    print('Suspicious looking maxima!')
elif numpy.sum(numpy.amin(data, axis=0)) == 0:
    print('Minima add up to zero! -> HEALTHY PARTICIPANT ALERT!')
else:
    print('Seems OK!')
```

    Minima add up to zero! -> HEALTHY PARTICIPANT ALERT!


## Functions
Defining functions


```python
fahrenheit_val = 99
celsius_val = ((fahrenheit_val - 32) * (5/9))

print(celsius_val)
```

    37.22222222222222



```python
def explicit_fahr_to_celsius(temp):
    # Assign converted value to variable
    converted = ((temp - 32) * (5/9))
    # Return value of new variable
    return converted
```


```python
def fahr_to_celsius(temp):
    # More efficient function without creating a new variable
    return ((temp -32) * (5/9))
```


```python
fahr_to_celsius(32)
```




    0.0




```python
explicit_fahr_to_celsius(32)
```




    0.0




```python
print('Freezing point of water:', fahr_to_celsius(32), 'C')
print('Boiling point of water:', fahr_to_celsius(212), 'C')
```

    Freezing point of water: 0.0 C
    Boiling point of water: 100.0 C



```python
def celsius_to_kelvin(temp_c):
    return temp_c + 273.15
print('Freezing point of water in Kelvin:', celsius_to_kelvin(0.))
```

    Freezing point of water in Kelvin: 273.15



```python
def fahr_to_kelvin(temp_f):
    temp_c = fahr_to_celsius(temp_f)
    temp_k = celsius_to_kelvin(temp_c)
    return temp_k

print('Boiling point of water in Kelvin:', fahr_to_kelvin(212.0))
```

    Boiling point of water in Kelvin: 373.15



```python
temp_kelvin = fahr_to_kelvin(212)
print('Temperature in Kelvin was:', temp_kelvin)
```

    Temperature in Kelvin was: 373.15



```python
def print_temperatures():
    print('Temperature in Fahrenheit was:', temp_fahr)
    print('Temperature in Kelvin was:', temp_kelvin)

temp_fahr = 212.0
temp_kelvin = fahr_to_kelvin(temp_fahr)

print_temperatures()
```

    Temperature in Fahrenheit was: 212.0
    Temperature in Kelvin was: 373.15

### Part 2: Using Actual Data
Putting it into practice, using the same inflammation data from previous exercises.


```python
import numpy
import matplotlib.pyplot
import glob
```


```python
def visualize(filename):
    data = numpy.loadtxt(fname = filename, delimiter = ',')
    
    fig = matplotlib.pyplot.figure(figsize= (10.0, 3.0))
    
    axes1 = fig.add_subplot(1, 3, 1)
    axes2 = fig.add_subplot(1, 3, 2)
    axes3 = fig.add_subplot(1, 3, 3)
    
    axes1.set_ylabel('Average')
    axes1.plot(numpy.mean(data, axis=0))
    
    axes2.set_ylabel('Max')
    axes2.plot(numpy.mean(data, axis=0))
    
    axes3.set_ylabel('Min')
    axes3.plot(numpy.mean(data, axis=0))
    
    fig.tight_layout()
    matplotlib.pyplot.show()
```


```python
def detect_problems(filename):
    data = numpy.loadtxt(fname = filename, delimiter = ',')
    
    if numpy.amax(data, axis = 0)[0] == 0 and numpy.amax(data, axis=0)[20] == 20:
        print("Suspicious looking maxima!")
    elif numpy.sum(numpy.amin(data, axis=0)) == 0:
        print('Minima add up to zero!')
    else:
        print('Seems ok!')
```


```python
filenames = sorted(glob.glob('inflammation*.csv'))

for filename in filenames:
    print(filename)
    visualize(filename)
    detect_problems(filename)
```

    inflammation-01.csv


![output_3_1](https://github.com/rjpellegr/RJP023_Python_Portfolio/assets/134185456/bdc5a9c1-ff13-4353-bbd0-0b285a65280e)


    Suspicious looking maxima!
    inflammation-02.csv


![output_3_3](https://github.com/rjpellegr/RJP023_Python_Portfolio/assets/134185456/e80960e1-695e-415a-bdb8-7a5625389f6d)


    Suspicious looking maxima!
    inflammation-03.csv


![output_3_5](https://github.com/rjpellegr/RJP023_Python_Portfolio/assets/134185456/63726c3e-ccc1-4889-a514-811b6465d4a1)


    Minima add up to zero!
    inflammation-04.csv


![output_3_7](https://github.com/rjpellegr/RJP023_Python_Portfolio/assets/134185456/24d61706-c791-4c54-9429-cbe084de79f0)


    Suspicious looking maxima!
    inflammation-05.csv


![output_3_9](https://github.com/rjpellegr/RJP023_Python_Portfolio/assets/134185456/72adf0a7-a7b2-4f3f-9c17-e586bf4882de)


    Suspicious looking maxima!
    inflammation-06.csv


![output_3_11](https://github.com/rjpellegr/RJP023_Python_Portfolio/assets/134185456/f15defa1-2b98-4526-bb18-0569a1755d2f)


    Suspicious looking maxima!
    inflammation-07.csv


![output_3_13](https://github.com/rjpellegr/RJP023_Python_Portfolio/assets/134185456/3378e9ff-3dfd-437f-bf8c-2e3ee2585922)


    Suspicious looking maxima!
    inflammation-08.csv


![output_3_15](https://github.com/rjpellegr/RJP023_Python_Portfolio/assets/134185456/f9013a39-85d5-48a6-a27a-312f1d719550)


    Minima add up to zero!
    inflammation-09.csv


![output_3_17](https://github.com/rjpellegr/RJP023_Python_Portfolio/assets/134185456/b2a576f3-9bd5-4e58-b99d-a0c9157e9886)


    Suspicious looking maxima!
    inflammation-10.csv


![output_3_19](https://github.com/rjpellegr/RJP023_Python_Portfolio/assets/134185456/5becd1db-f4ca-4a73-a1e2-18714935286d)


    Suspicious looking maxima!
    inflammation-11.csv


![output_3_21](https://github.com/rjpellegr/RJP023_Python_Portfolio/assets/134185456/51c6b550-a2fb-42b9-9b8d-8d7208eb0ba5)


    Minima add up to zero!
    inflammation-12.csv


![output_3_23](https://github.com/rjpellegr/RJP023_Python_Portfolio/assets/134185456/20e67437-377a-4340-bec0-232f10245a83)


    Suspicious looking maxima!



```python
def offset_mean(data, target_mean_value):
    return (data - numpy.mean(data)) + target_mean_value
```


```python
z = numpy.zeros((2,2))
print(offset_mean(z, 3))
```

    [[3. 3.]
     [3. 3.]]



```python
data = numpy.loadtxt(fname = 'inflammation-01.csv', delimiter = ',')

print(offset_mean(data, 0))
```

    [[-6.14875 -6.14875 -5.14875 ... -3.14875 -6.14875 -6.14875]
     [-6.14875 -5.14875 -4.14875 ... -5.14875 -6.14875 -5.14875]
     [-6.14875 -5.14875 -5.14875 ... -4.14875 -5.14875 -5.14875]
     ...
     [-6.14875 -5.14875 -5.14875 ... -5.14875 -5.14875 -5.14875]
     [-6.14875 -6.14875 -6.14875 ... -6.14875 -4.14875 -6.14875]
     [-6.14875 -6.14875 -5.14875 ... -5.14875 -5.14875 -6.14875]]



```python
print('Original min, mean, and max are:', numpy.amin(data), numpy.mean(data), numpy.amax(data))
offset_data = offset_mean(data, 0)
print('Min, mean and max of offset data are:',
    numpy.amin(offset_data),
    numpy.mean(offset_data),
    numpy.amax(offset_data))
```

    Original min, mean, and max are: 0.0 6.14875 20.0
    Min, mean and max of offset data are: -6.14875 2.842170943040401e-16 13.85125



```python
print('std dev before and after:', numpy.std(data), numpy.std(offset_data))
```

    std dev before and after: 4.613833197118566 4.613833197118566



```python
print('Difference in standard deviation before and after:',
      numpy.std(data) - numpy.std(offset_data))
```

    Difference in standard deviation before and after: 0.0



```python
# offset_mean(data, target_mean_value):
# return a new array containing the original data with its mean offset to match the desired value
# this data should be inputted as measurements in columns and samples in rows
def offset_mean(data, target_mean_value):
    return (data - numpy.mean(data)) + target_mean_value
```


```python
def offset_mean(data, target_mean_value):
    """Return a new array containing the original data
    with its mean offset to match the desired value
    
    Examples
    ------------
    
    >>>offset_mean([1,2,3], 0)
    array([-1., 0., 1.])
    """
    return(data - numpy.mean(data)) + target_mean_value
```


```python
help(offset_mean)
```

    Help on function offset_mean in module __main__:
    
    offset_mean(data, target_mean_value)
        Return a new array containing the original data
        with its mean offset to match the desired value
        
        Examples
        ------------
        
        >>>offset_mean([1,2,3], 0)
        array([-1., 0., 1.])
    



```python
numpy.loadtxt('inflammation-01.csv', delimiter = ',')
```




    array([[0., 0., 1., ..., 3., 0., 0.],
           [0., 1., 2., ..., 1., 0., 1.],
           [0., 1., 1., ..., 2., 1., 1.],
           ...,
           [0., 1., 1., ..., 1., 1., 1.],
           [0., 0., 0., ..., 0., 2., 0.],
           [0., 0., 1., ..., 1., 1., 0.]])




```python
def offset_mean(data, target_mean_value = 0.0):
    """Return a new array containing the original data
    with its mean offset to match the desired value (0 by default).
    
    Examples
    ------------
    
    >>>offset_mean([1,2,3])
    array([-1., 0., 1.])
    """
    return(data - numpy.mean(data)) + target_mean_value
```


```python
test_data = numpy.zeros((2,2))
print(offset_mean(test_data, 3))
```

    [[3. 3.]
     [3. 3.]]



```python
print(offset_mean(test_data))
```

    [[0. 0.]
     [0. 0.]]



```python
def display(a=1, b=2, c=3):
    print('a:', a, 'b:', b, 'c:', c)
print('no parameters:')
display()
print('one parameter:')
display(55)
print('two paramters:')
display(55,66)
```

    no parameters:
    a: 1 b: 2 c: 3
    one parameter:
    a: 55 b: 2 c: 3
    two paramters:
    a: 55 b: 66 c: 3



```python
print('only setting the value of c')
display(c = 77)
```

    only setting the value of c
    a: 1 b: 2 c: 77



```python
help(numpy.loadtxt)
```

    Help on function loadtxt in module numpy:
    
    loadtxt(fname, dtype=<class 'float'>, comments='#', delimiter=None, converters=None, skiprows=0, usecols=None, unpack=False, ndmin=0, encoding='bytes', max_rows=None)
        Load data from a text file.
        
        Each row in the text file must have the same number of values.
        
        Parameters
        ----------
        fname : file, str, or pathlib.Path
            File, filename, or generator to read.  If the filename extension is
            ``.gz`` or ``.bz2``, the file is first decompressed. Note that
            generators should return byte strings for Python 3k.
        dtype : data-type, optional
            Data-type of the resulting array; default: float.  If this is a
            structured data-type, the resulting array will be 1-dimensional, and
            each row will be interpreted as an element of the array.  In this
            case, the number of columns used must match the number of fields in
            the data-type.
        comments : str or sequence of str, optional
            The characters or list of characters used to indicate the start of a
            comment. None implies no comments. For backwards compatibility, byte
            strings will be decoded as 'latin1'. The default is '#'.
        delimiter : str, optional
            The string used to separate values. For backwards compatibility, byte
            strings will be decoded as 'latin1'. The default is whitespace.
        converters : dict, optional
            A dictionary mapping column number to a function that will parse the
            column string into the desired value.  E.g., if column 0 is a date
            string: ``converters = {0: datestr2num}``.  Converters can also be
            used to provide a default value for missing data (but see also
            `genfromtxt`): ``converters = {3: lambda s: float(s.strip() or 0)}``.
            Default: None.
        skiprows : int, optional
            Skip the first `skiprows` lines, including comments; default: 0.
        usecols : int or sequence, optional
            Which columns to read, with 0 being the first. For example,
            ``usecols = (1,4,5)`` will extract the 2nd, 5th and 6th columns.
            The default, None, results in all columns being read.
        
            .. versionchanged:: 1.11.0
                When a single column has to be read it is possible to use
                an integer instead of a tuple. E.g ``usecols = 3`` reads the
                fourth column the same way as ``usecols = (3,)`` would.
        unpack : bool, optional
            If True, the returned array is transposed, so that arguments may be
            unpacked using ``x, y, z = loadtxt(...)``.  When used with a structured
            data-type, arrays are returned for each field.  Default is False.
        ndmin : int, optional
            The returned array will have at least `ndmin` dimensions.
            Otherwise mono-dimensional axes will be squeezed.
            Legal values: 0 (default), 1 or 2.
        
            .. versionadded:: 1.6.0
        encoding : str, optional
            Encoding used to decode the inputfile. Does not apply to input streams.
            The special value 'bytes' enables backward compatibility workarounds
            that ensures you receive byte arrays as results if possible and passes
            'latin1' encoded strings to converters. Override this value to receive
            unicode arrays and pass strings as input to converters.  If set to None
            the system default is used. The default value is 'bytes'.
        
            .. versionadded:: 1.14.0
        max_rows : int, optional
            Read `max_rows` lines of content after `skiprows` lines. The default
            is to read all the lines.
        
            .. versionadded:: 1.16.0
        
        Returns
        -------
        out : ndarray
            Data read from the text file.
        
        See Also
        --------
        load, fromstring, fromregex
        genfromtxt : Load data with missing values handled as specified.
        scipy.io.loadmat : reads MATLAB data files
        
        Notes
        -----
        This function aims to be a fast reader for simply formatted files.  The
        `genfromtxt` function provides more sophisticated handling of, e.g.,
        lines with missing values.
        
        .. versionadded:: 1.10.0
        
        The strings produced by the Python float.hex method can be used as
        input for floats.
        
        Examples
        --------
        >>> from io import StringIO   # StringIO behaves like a file object
        >>> c = StringIO(u"0 1\n2 3")
        >>> np.loadtxt(c)
        array([[0., 1.],
               [2., 3.]])
        
        >>> d = StringIO(u"M 21 72\nF 35 58")
        >>> np.loadtxt(d, dtype={'names': ('gender', 'age', 'weight'),
        ...                      'formats': ('S1', 'i4', 'f4')})
        array([(b'M', 21, 72.), (b'F', 35, 58.)],
              dtype=[('gender', 'S1'), ('age', '<i4'), ('weight', '<f4')])
        
        >>> c = StringIO(u"1,0,2\n3,0,4")
        >>> x, y = np.loadtxt(c, delimiter=',', usecols=(0, 2), unpack=True)
        >>> x
        array([1., 3.])
        >>> y
        array([2., 4.])
    



```python
numpy.loadtxt('inflammation-01.csv', delimiter = ',')
```




    array([[0., 0., 1., ..., 3., 0., 0.],
           [0., 1., 2., ..., 1., 0., 1.],
           [0., 1., 1., ..., 2., 1., 1.],
           ...,
           [0., 1., 1., ..., 1., 1., 1.],
           [0., 0., 0., ..., 0., 2., 0.],
           [0., 0., 1., ..., 1., 1., 0.]])




```python
def s(p):
    s = 0
    for v in p:
        a += v
    m = a / len(p)
    d = 0
    for v in p:
        d += (v - m) * (v - m)
    return numpy.sqrt(d / len(p) - 1)

# same as above, but readable
def std_dev(sample):
    sample_sum = 0
    for value in sample:
        sample_sum += value

    sample_mean = sample_sum / len(sample)

    sum_squared_devs = 0
    for value in sample:
        sum_squared_devs += (value - sample_mean) * (value - sample_mean)

    return numpy.sqrt(sum_sqared_devs / len(sample) - 1)
```


## Defensive Programming
Using assertions as part of defensive programming strategies


```python
numbers = [1.5, 2.3, 0.7, 0.001, 4.4]
total = 0.0
for num in numbers:
    assert num > 0.0, 'Data should only contain positive values'
    total += num
print('total is:', total)
```

    total is: 8.901



```python
def normalize_rectangle(rect):
    """Normalizes a rectangle so that it is at the origin and 1.0 units long on its longest axis.
    Input should be of the format (x0, y0, x1, y1).
    (x0, y0) and (x1, y1) define the lower left and upper right corners of the recangle, respectively."""
    assert len(rect) == 4, 'Rectangles must contain 4 coordinates'
    x0, y0, x1, y1 = rect
    assert x0 < x1, 'Invalid X coordinates'
    assert y0 < y1, 'Invalid Y coordinates'

    dx = x1 - x0
    dy = y1 - y0
    if dx > dy:
        scaled = dx / dy
        upper_x, upper_y = 1.0, scaled
    else:
        scaled = dx / dy
        upper_x, upper_y = scaled, 1.0
    
    assert 0 < upper_x <= 1.0, 'Calculated upper x coordinate invalid'
    assert 0 < upper_y <= 1.0, 'Calculated upper y coordinate invalid'

    return(0, 0, upper_x, upper_y)
```


```python
print(normalize_rectangle((0.0, 1.0, 2.0)))
```


    ---------------------------------------------------------------------------

    AssertionError                            Traceback (most recent call last)

    <ipython-input-6-a81b6ed7619a> in <module>
    ----> 1 print(normalize_rectangle((0.0, 1.0, 2.0)))
    

    <ipython-input-5-4a7982d53b1a> in normalize_rectangle(rect)
          3     Input should be of the format (x0, y0, x1, y1).
          4     (x0, y0) and (x1, y1) define the lower left and upper right corners of the recangle, respectively."""
    ----> 5     assert len(rect) == 4, 'Rectangles must contain 4 coordinates'
          6     x0, y0, x1, y1 = rect
          7     assert x0 < x1, 'Invalid X coordinates'


    AssertionError: Rectangles must contain 4 coordinates



```python
print(normalize_rectangle((4.0, 2.0, 1.0, 5.0)))
```


    ---------------------------------------------------------------------------

    AssertionError                            Traceback (most recent call last)

    <ipython-input-7-5e28a32bada1> in <module>
    ----> 1 print(normalize_rectangle((4.0, 2.0, 1.0, 5.0)))
    

    <ipython-input-5-4a7982d53b1a> in normalize_rectangle(rect)
          5     assert len(rect) == 4, 'Rectangles must contain 4 coordinates'
          6     x0, y0, x1, y1 = rect
    ----> 7     assert x0 < x1, 'Invalid X coordinates'
          8     assert y0 < y1, 'Invalid Y coordinates'
          9 


    AssertionError: Invalid X coordinates



```python
print(normalize_rectangle((0.0, 0.0, 1.0, 5.0)))
```

    (0, 0, 0.2, 1.0)



```python
print(normalize_rectangle((0.0, 0.0, 5.0, 1.0)))
```


    ---------------------------------------------------------------------------

    AssertionError                            Traceback (most recent call last)

    <ipython-input-9-1337bef8f4bf> in <module>
    ----> 1 print(normalize_rectangle((0.0, 0.0, 5.0, 1.0)))
    

    <ipython-input-5-4a7982d53b1a> in normalize_rectangle(rect)
         18 
         19     assert 0 < upper_x <= 1.0, 'Calculated upper x coordinate invalid'
    ---> 20     assert 0 < upper_y <= 1.0, 'Calculated upper y coordinate invalid'
         21 
         22     return(0, 0, upper_x, upper_y)


    AssertionError: Calculated upper y coordinate invalid


## Transcribing DNA into RNA
A program that takes DNA sequences (formatted as a FASTA file) and produces the equivalent RNA sequence


```python
# Prompt user to enter the input FASTA file name

input_file_name = input("Input the name of the FASTA file to be transcribed: ")
```

    Input the name of the FASTA file to be transcribed:  UBC.txt



```python
# Open the input file and read the DNA sequence

with open(input_file_name, "r") as input_file:
    dna_sequence = ""
    for line in input_file:
        if line.startswith(">"):
            continue
        dna_sequence += line.strip()
```


```python
# Transcribe the DNA to RNA

rna_sequence = ""
for nucleotide in dna_sequence:
    if nucleotide == "T":
        rna_sequence += "U"
    else:
        rna_sequence += nucleotide
```


```python
# Prompt the user to enter the output file name

output_name = input("Enter the name of the ouput file: ")
```

    Enter the name of the ouput file:  Ubiquitin_C



```python
# Save the RNA sequence to a text file

with open(output_name, "w") as output_file:
    output_file.write(rna_sequence)
    print(f"The RNA sequence has been saved to {output_name}")
```

    The RNA sequence has been saved to Ubiquitin_C



```python
# Print the RNA sequence

print(rna_sequence)
```

    AUGCAGAUCUUCGUGAAGACUCUGACUGGUAAGACCAUCACCCUCGAGGUUGAGCCCAGUGACACCAUCGAGAAUGUCAAGGCAAAGAUCCAAGAUAAGGAAGGCAUCCCUCCUGACCAGCAGAGGCUGAUCUUUGCUGGAAAACAGCUGGAAGAUGGGCGCACCCUGUCUGACUACAACAUCCAGAAAGAGUCCACCCUGCACCUGGUGCUCCGUCUCAGAGGUGGGAUGCAAAUCUUCGUGAAGACACUCACUGGCAAGACCAUCACCCUUGAGGUCGAGCCCAGUGACACCAUCGAGAACGUCAAAGCAAAGAUCCAGGACAAGGAAGGCAUUCCUCCUGACCAGCAGAGGUUGAUCUUUGCCGGAAAGCAGCUGGAAGAUGGGCGCACCCUGUCUGACUACAACAUCCAGAAAGAGUCUACCCUGCACCUGGUGCUCCGUCUCAGAGGUGGGAUGCAGAUCUUCGUGAAGACCCUGACUGGUAAGACCAUCACCCUCGAGGUGGAGCCCAGUGACACCAUCGAGAAUGUCAAGGCAAAGAUCCAAGAUAAGGAAGGCAUUCCUCCUGAUCAGCAGAGGUUGAUCUUUGCCGGAAAACAGCUGGAAGAUGGUCGUACCCUGUCUGACUACAACAUCCAGAAAGAGUCCACCUUGCACCUGGUACUCCGUCUCAGAGGUGGGAUGCAAAUCUUCGUGAAGACACUCACUGGCAAGACCAUCACCCUUGAGGUCGAGCCCAGUGACACUAUCGAGAACGUCAAAGCAAAGAUCCAAGACAAGGAAGGCAUUCCUCCUGACCAGCAGAGGUUGAUCUUUGCCGGAAAGCAGCUGGAAGAUGGGCGCACCCUGUCUGACUACAACAUCCAGAAAGAGUCUACCCUGCACCUGGUGCUCCGUCUCAGAGGUGGGAUGCAGAUCUUCGUGAAGACCCUGACUGGUAAGACCAUCACUCUCGAAGUGGAGCCGAGUGACACCAUUGAGAAUGUCAAGGCAAAGAUCCAAGACAAGGAAGGCAUCCCUCCUGACCAGCAGAGGUUGAUCUUUGCCGGAAAACAGCUGGAAGAUGGUCGUACCCUGUCUGACUACAACAUCCAGAAAGAGUCCACCUUGCACCUGGUGCUCCGUCUCAGAGGUGGGAUGCAGAUCUUCGUGAAGACCCUGACUGGUAAGACCAUCACUCUCGAGGUGGAGCCGAGUGACACCAUUGAGAAUGUCAAGGCAAAGAUCCAAGACAAGGAAGGCAUCCCUCCUGACCAGCAGAGGUUGAUCUUUGCUGGGAAACAGCUGGAAGAUGGACGCACCCUGUCUGACUACAACAUCCAGAAAGAGUCCACCCUGCACCUGGUGCUCCGUCUUAGAGGUGGGAUGCAGAUCUUCGUGAAGACCCUGACUGGUAAGACCAUCACUCUCGAAGUGGAGCCGAGUGACACCAUUGAGAAUGUCAAGGCAAAGAUCCAAGACAAGGAAGGCAUCCCUCCUGACCAGCAGAGGUUGAUCUUUGCUGGGAAACAGCUGGAAGAUGGACGCACCCUGUCUGACUACAACAUCCAGAAAGAGUCCACCCUGCACCUGGUGCUCCGUCUUAGAGGUGGGAUGCAGAUCUUCGUGAAGACCCUGACUGGUAAGACCAUCACUCUCGAAGUGGAGCCGAGUGACACCAUUGAGAAUGUCAAGGCAAAGAUCCAAGACAAGGAAGGCAUCCCUCCUGACCAGCAGAGGUUGAUCUUUGCUGGGAAACAGCUGGAAGAUGGACGCACCCUGUCUGACUACAACAUCCAGAAAGAGUCCACCCUGCACCUGGUGCUCCGUCUCAGAGGUGGGAUGCAAAUCUUCGUGAAGACCCUGACUGGUAAGACCAUCACCCUCGAGGUGGAGCCCAGUGACACCAUCGAGAAUGUCAAGGCAAAGAUCCAAGAUAAGGAAGGCAUCCCUCCUGAUCAGCAGAGGUUGAUCUUUGCUGGGAAACAGCUGGAAGAUGGACGCACCCUGUCUGACUACAACAUCCAGAAAGAGUCCACUCUGCACUUGGUCCUGCGCUUGAGGGGGGGUGUCUAA



```python

```


## Translating RNA into Protein
A program that takes the RNA sequence created previously and translates it into the corresponding chain of amino acids (i.e. a protein)


```python
# Prompt user to enter the input RNA file name

input_name = input("Input the name of the file containing the RNA sequence to be translated: ")
```

    Input the name of the file containing the RNA sequence to be translated:  Ubiquitin_C



```python
# Open the file and read the RNA sequence

with open(input_name, "r") as input_file:
    rna_sequence = input_file.read().strip()
```


```python
# Define the codon table

codon_table = {
    "UUU": "F", "UUC": "F", "UUA": "L", "UUG": "L",
    "CUU": "L", "CUC": "L", "CUA": "L", "CUG": "L",
    "AUU": "I", "AUC": "I", "AUA": "I", "AUG": "M",
    "GUU": "V", "GUC": "V", "GUA": "V", "GUG": "V",
    "UCU": "S", "UCC": "S", "UCA": "S", "UCG": "S",
    "CCU": "P", "CCC": "P", "CCA": "P", "CCG": "P",
    "ACU": "T", "ACC": "T", "ACA": "T", "ACG": "T",
    "GCU": "A", "GCC": "A", "GCA": "A", "GCG": "A",
    "UAU": "Y", "UAC": "Y", "UAA": "*", "UAG": "*",
    "CAU": "H", "CAC": "H", "CAA": "Q", "CAG": "Q",
    "AAU": "N", "AAC": "N", "AAA": "K", "AAG": "K",
    "GAU": "D", "GAC": "D", "GAA": "E", "GAG": "E",
    "UGU": "C", "UGC": "C", "UGA": "*", "UGG": "W",
    "CGU": "R", "CGC": "R", "CGA": "R", "CGG": "R",
    "AGU": "S", "AGC": "S", "AGA": "R", "AGG": "R",
    "GGU": "G", "GGC": "G", "GGA": "G", "GGG": "G"
}
```


```python
# Translate RNA to protein

protein_sequence = ""
for i in range(0, len(rna_sequence), 3):
    codon = rna_sequence[i:i+3]
    if len(codon) == 3:
        amino_acid = codon_table[codon]
        if amino_acid == "*":
            break
        protein_sequence += amino_acid
```


```python
# Prompt user to enter output file name

output_name = input("Enter the name of the output file: ")
```

    Enter the name of the output file:  UbiquitinC_Protein.txt



```python
# Save the protein sequence to a text file

with open(output_name, "w") as output_file:
    output_file.write(protein_sequence)
    print(f"The protein sequence has been saved to {output_name}")
```

    The protein sequence has been saved to UbiquitinC_Protein.txt



```python
# Print the protein sequence

print(protein_sequence)
```

    MQIFVKTLTGKTITLEVEPSDTIENVKAKIQDKEGIPPDQQRLIFAGKQLEDGRTLSDYNIQKESTLHLVLRLRGGMQIFVKTLTGKTITLEVEPSDTIENVKAKIQDKEGIPPDQQRLIFAGKQLEDGRTLSDYNIQKESTLHLVLRLRGGMQIFVKTLTGKTITLEVEPSDTIENVKAKIQDKEGIPPDQQRLIFAGKQLEDGRTLSDYNIQKESTLHLVLRLRGGMQIFVKTLTGKTITLEVEPSDTIENVKAKIQDKEGIPPDQQRLIFAGKQLEDGRTLSDYNIQKESTLHLVLRLRGGMQIFVKTLTGKTITLEVEPSDTIENVKAKIQDKEGIPPDQQRLIFAGKQLEDGRTLSDYNIQKESTLHLVLRLRGGMQIFVKTLTGKTITLEVEPSDTIENVKAKIQDKEGIPPDQQRLIFAGKQLEDGRTLSDYNIQKESTLHLVLRLRGGMQIFVKTLTGKTITLEVEPSDTIENVKAKIQDKEGIPPDQQRLIFAGKQLEDGRTLSDYNIQKESTLHLVLRLRGGMQIFVKTLTGKTITLEVEPSDTIENVKAKIQDKEGIPPDQQRLIFAGKQLEDGRTLSDYNIQKESTLHLVLRLRGGMQIFVKTLTGKTITLEVEPSDTIENVKAKIQDKEGIPPDQQRLIFAGKQLEDGRTLSDYNIQKESTLHLVLRLRGGV
