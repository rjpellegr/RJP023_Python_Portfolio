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

## Analyzing Data

## Storing Values in Lists

## Using Loops

## Using Multiple Files

## Making Choices

## Functions

## Defensive Programming

## Transcribing DNA into RNA

## Transcribing RNA into Protein
