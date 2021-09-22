# MyDemo
> Super demo for nbdev.


This file has become my README and also the index of your documentation.

Thanks to nbdev magic `nbdev_build_docs`, run as part of `make`. 

## Install

`pip install your_project_name`  <-- replace with `mydemo`...

## How to use

Fill me in please! Don't forget code examples:

```python
1+1
```




    2



Okay, sure...

Grab some data from the webs

```python
dataset = 'car_crashes'
try:
    import seaborn as sns
    df = sns.load_dataset(dataset)
except ModuleNotFoundError:
    df = pd.read_csv(f'https://raw.githubusercontent.com/mwaskom/seaborn-data/master/{dataset}.csv')
df.sample(5)
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
      <th>total</th>
      <th>speeding</th>
      <th>alcohol</th>
      <th>not_distracted</th>
      <th>no_previous</th>
      <th>ins_premium</th>
      <th>ins_losses</th>
      <th>abbrev</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>12</th>
      <td>15.3</td>
      <td>5.508</td>
      <td>4.437</td>
      <td>13.005</td>
      <td>14.994</td>
      <td>641.96</td>
      <td>82.75</td>
      <td>ID</td>
    </tr>
    <tr>
      <th>26</th>
      <td>21.4</td>
      <td>8.346</td>
      <td>9.416</td>
      <td>17.976</td>
      <td>18.190</td>
      <td>816.21</td>
      <td>85.15</td>
      <td>MT</td>
    </tr>
    <tr>
      <th>19</th>
      <td>15.1</td>
      <td>5.738</td>
      <td>4.530</td>
      <td>13.137</td>
      <td>12.684</td>
      <td>661.88</td>
      <td>96.57</td>
      <td>ME</td>
    </tr>
    <tr>
      <th>18</th>
      <td>20.5</td>
      <td>7.175</td>
      <td>6.765</td>
      <td>14.965</td>
      <td>20.090</td>
      <td>1281.55</td>
      <td>194.78</td>
      <td>LA</td>
    </tr>
    <tr>
      <th>13</th>
      <td>12.8</td>
      <td>4.608</td>
      <td>4.352</td>
      <td>12.032</td>
      <td>12.288</td>
      <td>803.11</td>
      <td>139.15</td>
      <td>IL</td>
    </tr>
  </tbody>
</table>
</div>



### Test our super demo function

Use our super demo function to check which columns are numeric:

```python
df.apply(is_numeric)
```




    total              True
    speeding           True
    alcohol            True
    not_distracted     True
    no_previous        True
    ins_premium        True
    ins_losses         True
    abbrev            False
    dtype: bool



Modules can do their own testing!

```python
assert is_numeric(df['speeding'])
```

Okay, this is `index.ipynb` aka the README, but still...

### The README?

Yes, this notebook generates `README.md`.

Just type `nbdev_build_docs`, or even easier `make` from the commandline.

```python
discretize(df)
```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-12-4003b7267902> in <module>
    ----> 1 discretize(df)
    

    NameError: name 'discretize' is not defined

