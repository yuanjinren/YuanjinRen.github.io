---
layout: post
title:  Data Science Unit 1
subtitle: Sprint Challenge 1
---

# Data Science Unit 1 Sprint Challenge 1

## Data Wrangling and Storytelling

Taming data from its raw form into informative insights and stories.

## Data Wrangling

In this Sprint Challenge you will first "wrangle" some data from [Gapminder](https://www.gapminder.org/about-gapminder/), a Swedish non-profit co-founded by Hans Rosling. "Gapminder produces free teaching resources making the world understandable based on reliable statistics."
- [Cell phones (total), by country and year](https://raw.githubusercontent.com/open-numbers/ddf--gapminder--systema_globalis/master/ddf--datapoints--cell_phones_total--by--geo--time.csv)
- [Population (total), by country and year](https://raw.githubusercontent.com/open-numbers/ddf--gapminder--systema_globalis/master/ddf--datapoints--population_total--by--geo--time.csv)
- [Geo country codes](https://github.com/open-numbers/ddf--gapminder--systema_globalis/blob/master/ddf--entities--geo--country.csv)

These two links have everything you need to successfully complete the first part of this sprint challenge.
- [Pandas documentation: Working with Text Data](https://pandas.pydata.org/pandas-docs/stable/text.html) (one question)
- [Pandas Cheat Sheet](https://github.com/pandas-dev/pandas/blob/master/doc/cheatsheet/Pandas_Cheat_Sheet.pdf) (everything else)

### Part 1 - Load and Explore the Data

Run the cell below to load the datasets into three dataframes and then follow the instructions below



```python
import pandas as pd

cell_phones = pd.read_csv('https://raw.githubusercontent.com/open-numbers/ddf--gapminder--systema_globalis/master/ddf--datapoints--cell_phones_total--by--geo--time.csv')

population = pd.read_csv('https://raw.githubusercontent.com/open-numbers/ddf--gapminder--systema_globalis/master/ddf--datapoints--population_total--by--geo--time.csv')

geo_country_codes = (pd.read_csv('https://raw.githubusercontent.com/open-numbers/ddf--gapminder--systema_globalis/master/ddf--entities--geo--country.csv')
                       .rename(columns={'country': 'geo', 'name': 'country'}))

geo_country_codes = geo_country_codes[['geo','country']]
```


```python
cell_phones.head()
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
      <th>geo</th>
      <th>time</th>
      <th>cell_phones_total</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>abw</td>
      <td>1960</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>abw</td>
      <td>1965</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>abw</td>
      <td>1970</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>abw</td>
      <td>1975</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>abw</td>
      <td>1976</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Filter the cell_phones dataframe to only include information about the USA and China and then remake the scatterplot
usa_cell = cell_phones[cell_phones['geo'] == 'usa']
chn_cell = cell_phones[cell_phones['geo'] == 'chn']
chn_cell.head()
usa_chn_cell = pd.concat([usa_cell,chn_cell],axis=0)
usa_chn_cell
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
      <th>geo</th>
      <th>time</th>
      <th>cell_phones_total</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>8663</th>
      <td>usa</td>
      <td>1960</td>
      <td>0.000000e+00</td>
    </tr>
    <tr>
      <th>8664</th>
      <td>usa</td>
      <td>1965</td>
      <td>0.000000e+00</td>
    </tr>
    <tr>
      <th>8665</th>
      <td>usa</td>
      <td>1970</td>
      <td>0.000000e+00</td>
    </tr>
    <tr>
      <th>8666</th>
      <td>usa</td>
      <td>1975</td>
      <td>0.000000e+00</td>
    </tr>
    <tr>
      <th>8667</th>
      <td>usa</td>
      <td>1976</td>
      <td>0.000000e+00</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1606</th>
      <td>chn</td>
      <td>2013</td>
      <td>1.229113e+09</td>
    </tr>
    <tr>
      <th>1607</th>
      <td>chn</td>
      <td>2014</td>
      <td>1.286093e+09</td>
    </tr>
    <tr>
      <th>1608</th>
      <td>chn</td>
      <td>2015</td>
      <td>1.291984e+09</td>
    </tr>
    <tr>
      <th>1609</th>
      <td>chn</td>
      <td>2016</td>
      <td>1.364934e+09</td>
    </tr>
    <tr>
      <th>1610</th>
      <td>chn</td>
      <td>2017</td>
      <td>1.474097e+09</td>
    </tr>
  </tbody>
</table>
<p>89 rows × 3 columns</p>
</div>




```python
usa_chn_cell.plot.scatter('time','cell_phones_total');
```


![png](output_6_0.png)



```python
population.head()
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
      <th>geo</th>
      <th>time</th>
      <th>population_total</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>afg</td>
      <td>1800</td>
      <td>3280000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>afg</td>
      <td>1801</td>
      <td>3280000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>afg</td>
      <td>1802</td>
      <td>3280000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>afg</td>
      <td>1803</td>
      <td>3280000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>afg</td>
      <td>1804</td>
      <td>3280000</td>
    </tr>
  </tbody>
</table>
</div>



Check for missing/null values in the three dataframes


```python
# Your Work Here
cell_phones.isnull().sum()
```




    geo                  0
    time                 0
    cell_phones_total    0
    dtype: int64




```python
population.isnull().sum()
```




    geo                 0
    time                0
    population_total    0
    dtype: int64




```python
geo_country_codes.isnull().sum()
```




    geo        0
    country    0
    dtype: int64



Make a scatter plot from the `cell_phones` dataframe plotting "time" against "cell_phones_total"


```python
# Your Work Here
cell_phones.plot.scatter('time','cell_phones_total');
```


![png](output_13_0.png)


### Part 2 - Join data

First, join the `cell_phones` and `population` dataframes (with an inner join on `geo` and `time`).

The resulting dataframe's shape should be: (8590, 4)


```python
# Your Work Here
merged = pd.merge(cell_phones, population, how='inner', on=['geo', 'time'] )
merged
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
      <th>geo</th>
      <th>time</th>
      <th>cell_phones_total</th>
      <th>population_total</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>afg</td>
      <td>1960</td>
      <td>0.0</td>
      <td>8996967</td>
    </tr>
    <tr>
      <th>1</th>
      <td>afg</td>
      <td>1965</td>
      <td>0.0</td>
      <td>9956318</td>
    </tr>
    <tr>
      <th>2</th>
      <td>afg</td>
      <td>1970</td>
      <td>0.0</td>
      <td>11173654</td>
    </tr>
    <tr>
      <th>3</th>
      <td>afg</td>
      <td>1975</td>
      <td>0.0</td>
      <td>12689164</td>
    </tr>
    <tr>
      <th>4</th>
      <td>afg</td>
      <td>1976</td>
      <td>0.0</td>
      <td>12943093</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>8585</th>
      <td>zwe</td>
      <td>2013</td>
      <td>13633167.0</td>
      <td>13350378</td>
    </tr>
    <tr>
      <th>8586</th>
      <td>zwe</td>
      <td>2014</td>
      <td>11798652.0</td>
      <td>13586710</td>
    </tr>
    <tr>
      <th>8587</th>
      <td>zwe</td>
      <td>2015</td>
      <td>12757410.0</td>
      <td>13814642</td>
    </tr>
    <tr>
      <th>8588</th>
      <td>zwe</td>
      <td>2016</td>
      <td>12878926.0</td>
      <td>14030338</td>
    </tr>
    <tr>
      <th>8589</th>
      <td>zwe</td>
      <td>2017</td>
      <td>14092104.0</td>
      <td>14236599</td>
    </tr>
  </tbody>
</table>
<p>8590 rows × 4 columns</p>
</div>



Then, select the `geo` and `country` columns from the `geo_country_codes` dataframe, and join with your population and cell phone data.

The resulting dataframe's shape should be: (8590, 5)


```python
# Your Work Here
geo_country_codes[['geo','country']].head()
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
      <th>geo</th>
      <th>country</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>abkh</td>
      <td>Abkhazia</td>
    </tr>
    <tr>
      <th>1</th>
      <td>abw</td>
      <td>Aruba</td>
    </tr>
    <tr>
      <th>2</th>
      <td>afg</td>
      <td>Afghanistan</td>
    </tr>
    <tr>
      <th>3</th>
      <td>ago</td>
      <td>Angola</td>
    </tr>
    <tr>
      <th>4</th>
      <td>aia</td>
      <td>Anguilla</td>
    </tr>
  </tbody>
</table>
</div>




```python
merged2 = pd.merge(merged, geo_country_codes, how='inner', on='geo')
merged2
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
      <th>geo</th>
      <th>time</th>
      <th>cell_phones_total</th>
      <th>population_total</th>
      <th>country</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>afg</td>
      <td>1960</td>
      <td>0.0</td>
      <td>8996967</td>
      <td>Afghanistan</td>
    </tr>
    <tr>
      <th>1</th>
      <td>afg</td>
      <td>1965</td>
      <td>0.0</td>
      <td>9956318</td>
      <td>Afghanistan</td>
    </tr>
    <tr>
      <th>2</th>
      <td>afg</td>
      <td>1970</td>
      <td>0.0</td>
      <td>11173654</td>
      <td>Afghanistan</td>
    </tr>
    <tr>
      <th>3</th>
      <td>afg</td>
      <td>1975</td>
      <td>0.0</td>
      <td>12689164</td>
      <td>Afghanistan</td>
    </tr>
    <tr>
      <th>4</th>
      <td>afg</td>
      <td>1976</td>
      <td>0.0</td>
      <td>12943093</td>
      <td>Afghanistan</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>8585</th>
      <td>zwe</td>
      <td>2013</td>
      <td>13633167.0</td>
      <td>13350378</td>
      <td>Zimbabwe</td>
    </tr>
    <tr>
      <th>8586</th>
      <td>zwe</td>
      <td>2014</td>
      <td>11798652.0</td>
      <td>13586710</td>
      <td>Zimbabwe</td>
    </tr>
    <tr>
      <th>8587</th>
      <td>zwe</td>
      <td>2015</td>
      <td>12757410.0</td>
      <td>13814642</td>
      <td>Zimbabwe</td>
    </tr>
    <tr>
      <th>8588</th>
      <td>zwe</td>
      <td>2016</td>
      <td>12878926.0</td>
      <td>14030338</td>
      <td>Zimbabwe</td>
    </tr>
    <tr>
      <th>8589</th>
      <td>zwe</td>
      <td>2017</td>
      <td>14092104.0</td>
      <td>14236599</td>
      <td>Zimbabwe</td>
    </tr>
  </tbody>
</table>
<p>8590 rows × 5 columns</p>
</div>



### Part 3 - Make features

Calculate the number of cell phones per person, and add this column onto your dataframe.

(You've calculated correctly if you get 1.220 cell phones per person in the United States in 2017.)


```python
# Your Work Here 
merged2['cell_phone_person'] = merged2['cell_phones_total'] / merged2['population_total']
merged2
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
      <th>geo</th>
      <th>time</th>
      <th>cell_phones_total</th>
      <th>population_total</th>
      <th>country</th>
      <th>cell_phone_person</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>afg</td>
      <td>1960</td>
      <td>0.0</td>
      <td>8996967</td>
      <td>Afghanistan</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>afg</td>
      <td>1965</td>
      <td>0.0</td>
      <td>9956318</td>
      <td>Afghanistan</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>afg</td>
      <td>1970</td>
      <td>0.0</td>
      <td>11173654</td>
      <td>Afghanistan</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>afg</td>
      <td>1975</td>
      <td>0.0</td>
      <td>12689164</td>
      <td>Afghanistan</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>afg</td>
      <td>1976</td>
      <td>0.0</td>
      <td>12943093</td>
      <td>Afghanistan</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>8585</th>
      <td>zwe</td>
      <td>2013</td>
      <td>13633167.0</td>
      <td>13350378</td>
      <td>Zimbabwe</td>
      <td>1.021182</td>
    </tr>
    <tr>
      <th>8586</th>
      <td>zwe</td>
      <td>2014</td>
      <td>11798652.0</td>
      <td>13586710</td>
      <td>Zimbabwe</td>
      <td>0.868397</td>
    </tr>
    <tr>
      <th>8587</th>
      <td>zwe</td>
      <td>2015</td>
      <td>12757410.0</td>
      <td>13814642</td>
      <td>Zimbabwe</td>
      <td>0.923470</td>
    </tr>
    <tr>
      <th>8588</th>
      <td>zwe</td>
      <td>2016</td>
      <td>12878926.0</td>
      <td>14030338</td>
      <td>Zimbabwe</td>
      <td>0.917934</td>
    </tr>
    <tr>
      <th>8589</th>
      <td>zwe</td>
      <td>2017</td>
      <td>14092104.0</td>
      <td>14236599</td>
      <td>Zimbabwe</td>
      <td>0.989850</td>
    </tr>
  </tbody>
</table>
<p>8590 rows × 6 columns</p>
</div>




```python
condition = (merged2['time'] == 2017) & (merged2['country'] == 'United States')
checked = merged2[condition]
checked
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
      <th>geo</th>
      <th>time</th>
      <th>cell_phones_total</th>
      <th>population_total</th>
      <th>country</th>
      <th>cell_phone_person</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>8134</th>
      <td>usa</td>
      <td>2017</td>
      <td>395881000.0</td>
      <td>325084758</td>
      <td>United States</td>
      <td>1.217778</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Modify the geo column to make the geo codes uppercase instead of lowercase
merged2['geo'] = merged2['geo'].str.upper()
merged2['geo'].head()
```




    0    AFG
    1    AFG
    2    AFG
    3    AFG
    4    AFG
    Name: geo, dtype: object




```python
# 2014 was the first year that US had more cell phones than people
usa_check_df = merged2[merged2['country'] == 'United States']
condition4 = (usa_check_df['cell_phones_total']>=usa_check_df['population_total'])
new_usa_check_df = usa_check_df[condition4].sort_values(by='time')
new_usa_check_df
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
      <th>geo</th>
      <th>time</th>
      <th>cell_phones_total</th>
      <th>population_total</th>
      <th>country</th>
      <th>cell_phone_person</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>8131</th>
      <td>USA</td>
      <td>2014</td>
      <td>355500000.0</td>
      <td>318673422</td>
      <td>United States</td>
      <td>1.115562</td>
    </tr>
    <tr>
      <th>8132</th>
      <td>USA</td>
      <td>2015</td>
      <td>382307000.0</td>
      <td>320878312</td>
      <td>United States</td>
      <td>1.191439</td>
    </tr>
    <tr>
      <th>8133</th>
      <td>USA</td>
      <td>2016</td>
      <td>395881000.0</td>
      <td>323015992</td>
      <td>United States</td>
      <td>1.225577</td>
    </tr>
    <tr>
      <th>8134</th>
      <td>USA</td>
      <td>2017</td>
      <td>395881000.0</td>
      <td>325084758</td>
      <td>United States</td>
      <td>1.217778</td>
    </tr>
  </tbody>
</table>
</div>



### Part 4 - Process data

Use the describe function, to describe your dataframe's numeric columns, and then its non-numeric columns.

(You'll see the time period ranges from 1960 to 2017, and there are 195 unique countries represented.)


```python
# Your Work Here
merged2.describe()    #numeric columns
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
      <th>time</th>
      <th>cell_phones_total</th>
      <th>population_total</th>
      <th>cell_phone_person</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>8590.000000</td>
      <td>8.590000e+03</td>
      <td>8.590000e+03</td>
      <td>8590.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>1994.193481</td>
      <td>9.004950e+06</td>
      <td>2.982872e+07</td>
      <td>0.280819</td>
    </tr>
    <tr>
      <th>std</th>
      <td>14.257975</td>
      <td>5.573408e+07</td>
      <td>1.165793e+08</td>
      <td>0.455745</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1960.000000</td>
      <td>0.000000e+00</td>
      <td>4.377000e+03</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>1983.000000</td>
      <td>0.000000e+00</td>
      <td>1.450626e+06</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>1995.000000</td>
      <td>6.200000e+03</td>
      <td>5.763844e+06</td>
      <td>0.001561</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>2006.000000</td>
      <td>1.697652e+06</td>
      <td>1.807534e+07</td>
      <td>0.463197</td>
    </tr>
    <tr>
      <th>max</th>
      <td>2017.000000</td>
      <td>1.474097e+09</td>
      <td>1.421022e+09</td>
      <td>2.510205</td>
    </tr>
  </tbody>
</table>
</div>




```python
merged2.describe(exclude = 'number')   #non-numeric columns
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
      <th>geo</th>
      <th>country</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>8590</td>
      <td>8590</td>
    </tr>
    <tr>
      <th>unique</th>
      <td>195</td>
      <td>195</td>
    </tr>
    <tr>
      <th>top</th>
      <td>swe</td>
      <td>United Kingdom</td>
    </tr>
    <tr>
      <th>freq</th>
      <td>46</td>
      <td>46</td>
    </tr>
  </tbody>
</table>
</div>



In 2017, what were the top 5 countries with the most cell phones total?

Your list of countries should have these totals:

| country | cell phones total |
|:-------:|:-----------------:|
|    ?    |     1,474,097,000 |
|    ?    |     1,168,902,277 |
|    ?    |       458,923,202 |
|    ?    |       395,881,000 |
|    ?    |       236,488,548 |



```python
condition2 = (merged2['time'] == 2017)
checked2 = merged2[condition2]
checked2
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
      <th>geo</th>
      <th>time</th>
      <th>cell_phones_total</th>
      <th>population_total</th>
      <th>country</th>
      <th>cell_phone_person</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>45</th>
      <td>afg</td>
      <td>2017</td>
      <td>23929713.0</td>
      <td>36296111</td>
      <td>Afghanistan</td>
      <td>0.659291</td>
    </tr>
    <tr>
      <th>91</th>
      <td>ago</td>
      <td>2017</td>
      <td>13323952.0</td>
      <td>29816769</td>
      <td>Angola</td>
      <td>0.446861</td>
    </tr>
    <tr>
      <th>137</th>
      <td>alb</td>
      <td>2017</td>
      <td>3497950.0</td>
      <td>2884169</td>
      <td>Albania</td>
      <td>1.212810</td>
    </tr>
    <tr>
      <th>183</th>
      <td>and</td>
      <td>2017</td>
      <td>80337.0</td>
      <td>76997</td>
      <td>Andorra</td>
      <td>1.043378</td>
    </tr>
    <tr>
      <th>219</th>
      <td>are</td>
      <td>2017</td>
      <td>19826224.0</td>
      <td>9487206</td>
      <td>United Arab Emirates</td>
      <td>2.089785</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>8363</th>
      <td>vut</td>
      <td>2017</td>
      <td>228016.0</td>
      <td>285499</td>
      <td>Vanuatu</td>
      <td>0.798658</td>
    </tr>
    <tr>
      <th>8406</th>
      <td>wsm</td>
      <td>2017</td>
      <td>124211.0</td>
      <td>195358</td>
      <td>Samoa</td>
      <td>0.635812</td>
    </tr>
    <tr>
      <th>8497</th>
      <td>zaf</td>
      <td>2017</td>
      <td>91878275.0</td>
      <td>57009751</td>
      <td>South Africa</td>
      <td>1.611624</td>
    </tr>
    <tr>
      <th>8543</th>
      <td>zmb</td>
      <td>2017</td>
      <td>13438539.0</td>
      <td>16853608</td>
      <td>Zambia</td>
      <td>0.797369</td>
    </tr>
    <tr>
      <th>8589</th>
      <td>zwe</td>
      <td>2017</td>
      <td>14092104.0</td>
      <td>14236599</td>
      <td>Zimbabwe</td>
      <td>0.989850</td>
    </tr>
  </tbody>
</table>
<p>168 rows × 6 columns</p>
</div>




```python
# Your Work Here
result = checked2.sort_values(by='cell_phones_total',ascending=False)
result[['country','cell_phones_total']].head(5)
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
      <th>country</th>
      <th>cell_phones_total</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1496</th>
      <td>China</td>
      <td>1.474097e+09</td>
    </tr>
    <tr>
      <th>3595</th>
      <td>India</td>
      <td>1.168902e+09</td>
    </tr>
    <tr>
      <th>3549</th>
      <td>Indonesia</td>
      <td>4.589232e+08</td>
    </tr>
    <tr>
      <th>8134</th>
      <td>United States</td>
      <td>3.958810e+08</td>
    </tr>
    <tr>
      <th>1084</th>
      <td>Brazil</td>
      <td>2.364885e+08</td>
    </tr>
  </tbody>
</table>
</div>



## Data Storytelling

In this part of the sprint challenge you'll work with a dataset from **FiveThirtyEight's article, [Every Guest Jon Stewart Ever Had On ‘The Daily Show’](https://fivethirtyeight.com/features/every-guest-jon-stewart-ever-had-on-the-daily-show/)**!

### Part 0 — Run this starter code

You don't need to add or change anything here. Just run this cell and it loads the data for you, into a dataframe named `df`.

(You can explore the data if you want, but it's not required to pass the Sprint Challenge.)


```python
%matplotlib inline
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd
import seaborn as sns

cable_news_url = 'https://raw.githubusercontent.com/fivethirtyeight/data/master/media-mentions-2020/cable_weekly.csv'
online_news_url = 'https://raw.githubusercontent.com/fivethirtyeight/data/master/media-mentions-2020/online_weekly.csv'

cable = pd.read_csv(cable_news_url)
online = pd.read_csv(online_news_url)

merged = pd.merge(cable[['date', 'name', 'pct_of_all_candidate_clips']], online[['date', 'name', 'pct_of_all_candidate_stories']])
merged['date'] = pd.to_datetime(merged['date'], infer_datetime_format=True)
merged = merged.set_index('date')

unique_dates = list(set(merged.index.to_list()))

import datetime

joe_biden_cable_multiple = []
joe_biden_online_multiple = []

for date in unique_dates:
  that_day = merged.loc[datetime.date(year=date.year, month=date.month, day=date.day)]

  joe_biden_cable_that_day = that_day[that_day['name']=="Joe Biden"]['pct_of_all_candidate_clips']
  not_joe_biden_cable_max = that_day[that_day['name']!="Joe Biden"]['pct_of_all_candidate_clips'].max()
  joe_biden_cable_multiple_of_max = joe_biden_cable_that_day / not_joe_biden_cable_max

  joe_biden_online_that_day = that_day[that_day['name']=="Joe Biden"]['pct_of_all_candidate_stories']
  not_joe_biden_online_max = that_day[that_day['name']!="Joe Biden"]['pct_of_all_candidate_stories'].max()
  joe_biden_online_multiple_of_max = joe_biden_online_that_day / not_joe_biden_online_max


  joe_biden_cable_multiple.append(joe_biden_cable_multiple_of_max.values[0])
  joe_biden_online_multiple.append(joe_biden_online_multiple_of_max.values[0])

df = pd.DataFrame({'date': unique_dates, 'biden_cable_multiple':joe_biden_cable_multiple, 'biden_online_multiple': joe_biden_online_multiple})
df = df.set_index('date')
df = df.sort_index()

data_for_graph = df.loc[datetime.date(2019, 4, 15):]
print(data_for_graph.shape)
data_for_graph.head()
```

    (27, 2)





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
      <th>biden_cable_multiple</th>
      <th>biden_online_multiple</th>
    </tr>
    <tr>
      <th>date</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2019-04-21</th>
      <td>3.087352</td>
      <td>1.107492</td>
    </tr>
    <tr>
      <th>2019-04-28</th>
      <td>3.707641</td>
      <td>1.295820</td>
    </tr>
    <tr>
      <th>2019-05-05</th>
      <td>2.805169</td>
      <td>1.306122</td>
    </tr>
    <tr>
      <th>2019-05-12</th>
      <td>3.235849</td>
      <td>1.045386</td>
    </tr>
    <tr>
      <th>2019-05-19</th>
      <td>2.494624</td>
      <td>1.119588</td>
    </tr>
  </tbody>
</table>
</div>




```python
df
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
      <th>biden_cable_multiple</th>
      <th>biden_online_multiple</th>
    </tr>
    <tr>
      <th>date</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2018-12-30</th>
      <td>0.245492</td>
      <td>0.356659</td>
    </tr>
    <tr>
      <th>2019-01-06</th>
      <td>0.431604</td>
      <td>0.492401</td>
    </tr>
    <tr>
      <th>2019-01-13</th>
      <td>0.990476</td>
      <td>0.360000</td>
    </tr>
    <tr>
      <th>2019-01-20</th>
      <td>0.423497</td>
      <td>0.440758</td>
    </tr>
    <tr>
      <th>2019-01-27</th>
      <td>0.204420</td>
      <td>0.274752</td>
    </tr>
    <tr>
      <th>2019-02-03</th>
      <td>0.276596</td>
      <td>0.334471</td>
    </tr>
    <tr>
      <th>2019-02-10</th>
      <td>0.375824</td>
      <td>0.335766</td>
    </tr>
    <tr>
      <th>2019-02-17</th>
      <td>0.305101</td>
      <td>0.331754</td>
    </tr>
    <tr>
      <th>2019-02-24</th>
      <td>0.426205</td>
      <td>0.316879</td>
    </tr>
    <tr>
      <th>2019-03-03</th>
      <td>0.844530</td>
      <td>0.425787</td>
    </tr>
    <tr>
      <th>2019-03-10</th>
      <td>0.691954</td>
      <td>0.652755</td>
    </tr>
    <tr>
      <th>2019-03-17</th>
      <td>1.006897</td>
      <td>0.632721</td>
    </tr>
    <tr>
      <th>2019-03-24</th>
      <td>1.258824</td>
      <td>0.784211</td>
    </tr>
    <tr>
      <th>2019-03-31</th>
      <td>4.882033</td>
      <td>1.783109</td>
    </tr>
    <tr>
      <th>2019-04-07</th>
      <td>0.692771</td>
      <td>0.477987</td>
    </tr>
    <tr>
      <th>2019-04-14</th>
      <td>0.501031</td>
      <td>0.377119</td>
    </tr>
    <tr>
      <th>2019-04-21</th>
      <td>3.087352</td>
      <td>1.107492</td>
    </tr>
    <tr>
      <th>2019-04-28</th>
      <td>3.707641</td>
      <td>1.295820</td>
    </tr>
    <tr>
      <th>2019-05-05</th>
      <td>2.805169</td>
      <td>1.306122</td>
    </tr>
    <tr>
      <th>2019-05-12</th>
      <td>3.235849</td>
      <td>1.045386</td>
    </tr>
    <tr>
      <th>2019-05-19</th>
      <td>2.494624</td>
      <td>1.119588</td>
    </tr>
    <tr>
      <th>2019-05-26</th>
      <td>3.684211</td>
      <td>1.566434</td>
    </tr>
    <tr>
      <th>2019-06-02</th>
      <td>4.120773</td>
      <td>1.268581</td>
    </tr>
    <tr>
      <th>2019-06-09</th>
      <td>2.955257</td>
      <td>1.340233</td>
    </tr>
    <tr>
      <th>2019-06-16</th>
      <td>3.574713</td>
      <td>1.687805</td>
    </tr>
    <tr>
      <th>2019-06-23</th>
      <td>2.258354</td>
      <td>1.072789</td>
    </tr>
    <tr>
      <th>2019-06-30</th>
      <td>1.168615</td>
      <td>1.034346</td>
    </tr>
    <tr>
      <th>2019-07-07</th>
      <td>2.218236</td>
      <td>1.296041</td>
    </tr>
    <tr>
      <th>2019-07-14</th>
      <td>1.565041</td>
      <td>0.936975</td>
    </tr>
    <tr>
      <th>2019-07-21</th>
      <td>1.855072</td>
      <td>0.938650</td>
    </tr>
    <tr>
      <th>2019-07-28</th>
      <td>1.988069</td>
      <td>1.033973</td>
    </tr>
    <tr>
      <th>2019-08-04</th>
      <td>1.868519</td>
      <td>1.173984</td>
    </tr>
    <tr>
      <th>2019-08-11</th>
      <td>1.592424</td>
      <td>0.913628</td>
    </tr>
    <tr>
      <th>2019-08-18</th>
      <td>1.889323</td>
      <td>0.847244</td>
    </tr>
    <tr>
      <th>2019-08-25</th>
      <td>2.046753</td>
      <td>1.095238</td>
    </tr>
    <tr>
      <th>2019-09-01</th>
      <td>2.231672</td>
      <td>1.068441</td>
    </tr>
    <tr>
      <th>2019-09-08</th>
      <td>1.669750</td>
      <td>1.055731</td>
    </tr>
    <tr>
      <th>2019-09-15</th>
      <td>2.601589</td>
      <td>1.067506</td>
    </tr>
    <tr>
      <th>2019-09-22</th>
      <td>4.558233</td>
      <td>4.649776</td>
    </tr>
    <tr>
      <th>2019-09-29</th>
      <td>4.980180</td>
      <td>3.402359</td>
    </tr>
    <tr>
      <th>2019-10-06</th>
      <td>3.260229</td>
      <td>2.545723</td>
    </tr>
    <tr>
      <th>2019-10-13</th>
      <td>1.676190</td>
      <td>1.406303</td>
    </tr>
    <tr>
      <th>2019-10-20</th>
      <td>1.726508</td>
      <td>1.552770</td>
    </tr>
  </tbody>
</table>
</div>




```python
data_for_graph
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
      <th>biden_cable_multiple</th>
      <th>biden_online_multiple</th>
    </tr>
    <tr>
      <th>date</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2019-04-21</th>
      <td>3.087352</td>
      <td>1.107492</td>
    </tr>
    <tr>
      <th>2019-04-28</th>
      <td>3.707641</td>
      <td>1.295820</td>
    </tr>
    <tr>
      <th>2019-05-05</th>
      <td>2.805169</td>
      <td>1.306122</td>
    </tr>
    <tr>
      <th>2019-05-12</th>
      <td>3.235849</td>
      <td>1.045386</td>
    </tr>
    <tr>
      <th>2019-05-19</th>
      <td>2.494624</td>
      <td>1.119588</td>
    </tr>
    <tr>
      <th>2019-05-26</th>
      <td>3.684211</td>
      <td>1.566434</td>
    </tr>
    <tr>
      <th>2019-06-02</th>
      <td>4.120773</td>
      <td>1.268581</td>
    </tr>
    <tr>
      <th>2019-06-09</th>
      <td>2.955257</td>
      <td>1.340233</td>
    </tr>
    <tr>
      <th>2019-06-16</th>
      <td>3.574713</td>
      <td>1.687805</td>
    </tr>
    <tr>
      <th>2019-06-23</th>
      <td>2.258354</td>
      <td>1.072789</td>
    </tr>
    <tr>
      <th>2019-06-30</th>
      <td>1.168615</td>
      <td>1.034346</td>
    </tr>
    <tr>
      <th>2019-07-07</th>
      <td>2.218236</td>
      <td>1.296041</td>
    </tr>
    <tr>
      <th>2019-07-14</th>
      <td>1.565041</td>
      <td>0.936975</td>
    </tr>
    <tr>
      <th>2019-07-21</th>
      <td>1.855072</td>
      <td>0.938650</td>
    </tr>
    <tr>
      <th>2019-07-28</th>
      <td>1.988069</td>
      <td>1.033973</td>
    </tr>
    <tr>
      <th>2019-08-04</th>
      <td>1.868519</td>
      <td>1.173984</td>
    </tr>
    <tr>
      <th>2019-08-11</th>
      <td>1.592424</td>
      <td>0.913628</td>
    </tr>
    <tr>
      <th>2019-08-18</th>
      <td>1.889323</td>
      <td>0.847244</td>
    </tr>
    <tr>
      <th>2019-08-25</th>
      <td>2.046753</td>
      <td>1.095238</td>
    </tr>
    <tr>
      <th>2019-09-01</th>
      <td>2.231672</td>
      <td>1.068441</td>
    </tr>
    <tr>
      <th>2019-09-08</th>
      <td>1.669750</td>
      <td>1.055731</td>
    </tr>
    <tr>
      <th>2019-09-15</th>
      <td>2.601589</td>
      <td>1.067506</td>
    </tr>
    <tr>
      <th>2019-09-22</th>
      <td>4.558233</td>
      <td>4.649776</td>
    </tr>
    <tr>
      <th>2019-09-29</th>
      <td>4.980180</td>
      <td>3.402359</td>
    </tr>
    <tr>
      <th>2019-10-06</th>
      <td>3.260229</td>
      <td>2.545723</td>
    </tr>
    <tr>
      <th>2019-10-13</th>
      <td>1.676190</td>
      <td>1.406303</td>
    </tr>
    <tr>
      <th>2019-10-20</th>
      <td>1.726508</td>
      <td>1.552770</td>
    </tr>
  </tbody>
</table>
</div>




```python
data_for_graph.index
```




    DatetimeIndex(['2019-04-21', '2019-04-28', '2019-05-05', '2019-05-12',
                   '2019-05-19', '2019-05-26', '2019-06-02', '2019-06-09',
                   '2019-06-16', '2019-06-23', '2019-06-30', '2019-07-07',
                   '2019-07-14', '2019-07-21', '2019-07-28', '2019-08-04',
                   '2019-08-11', '2019-08-18', '2019-08-25', '2019-09-01',
                   '2019-09-08', '2019-09-15', '2019-09-22', '2019-09-29',
                   '2019-10-06', '2019-10-13', '2019-10-20'],
                  dtype='datetime64[ns]', name='date', freq=None)



### Part 1 — Recreate this explanatory visualization:




```python
from IPython.display import display, Image
png = 'https://fivethirtyeight.com/wp-content/uploads/2019/10/Mehta-Media1028-1028-1.png'
example = Image(png, width=500)
display(example)
```


![png](output_37_0.png)


**Hints:**
- You can choose any Python visualization library you want. I've verified the plot can be reproduced with matplotlib, pandas plot, or seaborn. I assume other libraries like altair or plotly would work too.

**Expectations:** Your plot should include:
- 2 lines visualizing the Cable news vs Online news lines The shapes of the lines should look roughly identical to 538's example. Each line should be a different color. (But you don't need to use the _same_ colors as 538.)
- Legend **or** labels for the lines. (But **you don't need each label positioned next to its line or colored like 538.**)
- Title in the upper left: _"Biden's Ukraine-related media bump is fading"_ with more visual emphasis than the subtitle. (Bolder and/or larger font.)
- Subtitle underneath the title: _"Biden's share of media mentions on each medium relative ot the next most-mentioned candidate each week"_


```python
plt.style.use('fivethirtyeight')
fig, ax= plt.subplots(figsize=(7, 5))
x = data_for_graph.index
y = data_for_graph['biden_cable_multiple'].tolist()
z = data_for_graph['biden_online_multiple'].tolist()
ax.plot(x,y,color='#42f5b6',linewidth=2.5)
ax.plot(x,z,color='#f59342',linewidth=2.5)
fig.set_facecolor('#f2f4f7')
ax.set(facecolor='#f2f4f7')
ax.set_xticklabels(["MAY'19","JUNE","JUL","AUG.","SEP.","OCT."], fontsize=9)
labels = ["0","EVEN","2","3","4","5x"]
ax.set_yticklabels(labels)
ax.set_title("Biden's Ukraine-related media bump is fading", fontsize=16, fontweight='bold',loc='left',x=-.06, y=1.3)
ax.spines['left'].set_visible(False)
ax.spines['right'].set_visible(False)
ax.spines['top'].set_visible(False)
ax.spines['bottom'].set_color('Black')
ax.text("2019-04-01",6.0,"Biden's share of media mentions on each medium relative ot the next" + "\n" + "most-mentioned candidate each week", fontsize=14);
ax.text("2019-06-10",4.5,"After the Ukraine new broke," + "\n" + "Biden was mentioned five times" +"\n" + "more than the next most-mentioned"+ "\n" + "candidate on cable news", fontsize=12, style='italic');
ax.text("2019-04-20",4,"Cable news",fontweight='bold');
ax.text("2019-04-10",1.5,"Online news",fontweight='bold');
```


![png](output_39_0.png)


## How to get a 3 on this Sprint Challenge:

Once you have completed the above making a solid attempt at each section, if you still have time remaining, you can go back and do any of the following to get a score of 3 on the above sections. Remember that everything in this section is **optional** and that we will average your scores between the different sections, so get the easy points first!

Complete any of the following **within** their corresponding sections in the Sprint Challenge (go back up and add these thigns):

### Data Wrangling Section 1

Filter the `cell_phones` dataframe to only include information about the USA and China and then remake the scatterplot. 

### Data Wrangling Section 2

Explain why we are using an "inner" join when we merge these dataframes. 

### Data Wrangling Section 3

Modify the geo column to make the geo codes uppercase instead of lowercase.

### Data Wrangling Section 4

2017 was the first year that China had more cell phones than people.

What was the first year that the USA had more cell phones than people?

### Data Storytelling 

Keep on working on your graph to make it look particularly like the 538 graph by manipulating the graph's background color, the line colors, the x and y axis tick marks/labels, etc. 

If you have already completed everything else, take this as far as you can within the time limit.


# New Section


```python

```

