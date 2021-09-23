# MyDemo
> Super demo for nbdev. We'll write a discretizer.


Normally this bit would describe the package, give Install instructions, and then some Examples.

But since this is an `nbdev` **demo**, I'll start by talking about using `nbdev`.  I'll assume by this time you have:

* Switched to a suitable Python virtual environment
* Installed jupyter
* Installed nbdev
* Found and maybe cloned this repo.

This README is written in `index.ipynb` which generates `README.md` and the `index.html` page in `docs/`.  Yes, you get to write README in Jupyter! 

* GitHub renders `README.md` as the main package description.
* It also creates and hosts full package documentation via GutHub Pages.
* Or you can see those locally if you install & run Jekyll.

In `index.ipynb`, assuming you've imported your module(s) up top (`from mydemo.core import *`), you can generate the `mydemo` Python package & docs via these two commands:

```
$ nbdev_build_lib && nbdev_build_docs
```

(If you have `make` installed, just type `make`!)



## Caveats
⚠️ The first cell should import your module(s). We just have one, named `core`. It's defined in `00_core.ipynb` which generates `mydemo/core.py`, which we import here as `from mydemo.core import *`, up in the first cell. 

⚠️ The "MyDemo" title cell should be (roughly) second, and has a _specific format_. Follow the template:

```python
   # ModuleName

   > One-line module description
```

⚠️ The `settings.ini` can be tricky. Remember to `require` key packages or it may not work in a new environment (so GitHub's Continuous Integration will fail).

## Install

Write your install instructions here. Typically something like:

`pip install your_project_name`  <-- replace with `mydemo`...

Note: `nbdev` makes it easy to upload your package to `pip` or `conda`, but if doing this for work, _check with work first!_.  Similarly with GitHub etc.  (Though you can configure `nbdev` to use private repositories.)

## How to use

Fill me in please! Don't forget code examples. 

OK, let's use our module's data-grabbing function to get car crash data. 

```python
df = getCrashes()
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
      <th>39</th>
      <td>11.1</td>
      <td>3.774</td>
      <td>4.218</td>
      <td>10.212</td>
      <td>8.769</td>
      <td>1148.99</td>
      <td>148.58</td>
      <td>RI</td>
    </tr>
    <tr>
      <th>2</th>
      <td>18.6</td>
      <td>6.510</td>
      <td>5.208</td>
      <td>15.624</td>
      <td>17.856</td>
      <td>899.47</td>
      <td>110.35</td>
      <td>AZ</td>
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
    <tr>
      <th>44</th>
      <td>11.3</td>
      <td>4.859</td>
      <td>1.808</td>
      <td>9.944</td>
      <td>10.848</td>
      <td>809.38</td>
      <td>109.48</td>
      <td>UT</td>
    </tr>
    <tr>
      <th>41</th>
      <td>19.4</td>
      <td>6.014</td>
      <td>6.402</td>
      <td>19.012</td>
      <td>16.684</td>
      <td>669.31</td>
      <td>96.87</td>
      <td>SD</td>
    </tr>
  </tbody>
</table>
</div>



### Test our super demo function

Core defines a few handy functions like `is_numeric()`. Try it:

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



It's common to put `assert` in some tests so `nbdev` can check during build.  (This is more common in the modules rather than the index/README.) Here:

```python
assert is_numeric(df['speeding'])
```

### Test the fancy `discretize()` function.

It will report its actions, and then return the discretized dataframe, suitable for passing on to your Bayes Net learning algorithm, etc. 

```python
help(discretize)
```

    Help on function discretize in module mydemo.core:
    
    discretize(df, nbins=10, cut=<function qcut at 0x7ff4a04a6440>, verbose=2, drop_useless=True)
        Discretize columns in {df} to have at most {nbins} categories.
          * Categorical columns: take the Top n-1 plus "Other"
          * Continuous columns: cut into {nbins} using {cut}.
        
        Returns a new discretized dataframe with the same column names.
        Promotes discrete columns to categories.
        
        Parameters
        -----------
        df: Dataframe to discretize
        nbins: Max number of bins to use. May return fewer.
        cut: Cutting method. Default `pd.qcut`. Consider pd.cut, or write your own.
        verbose: 0: silent, 1: colnames, 2: (Default) top N for each column
        drop_useless: Removes columns that have < 2 unique values.
        
        Replaces numerical NA values with 'NA'.
    


```python
discretize(df, nbins=4)
```

    total:
    	(5.899, 12.75]    13
    	(12.75, 15.6]     13
    	(15.6, 18.5]      12
    	(18.5, 23.9]      13
    speeding:
    	(1.7910000000000001, 3.766]    13
    	(3.766, 4.608]                 13
    	(4.608, 6.439]                 12
    	(6.439, 9.45]                  13
    alcohol:
    	(1.592, 3.894]     13
    	(3.894, 4.554]     13
    	(4.554, 5.604]     12
    	(5.604, 10.038]    13
    not_distracted:
    	(1.7590000000000001, 10.478]    13
    	(10.478, 13.857]                13
    	(13.857, 16.14]                 12
    	(16.14, 23.661]                 13
    no_previous:
    	(5.899, 11.348]     13
    	(11.348, 13.775]    13
    	(13.775, 16.755]    12
    	(16.755, 21.28]     13
    ins_premium:
    	(641.9590000000001, 768.43]    13
    	(768.43, 858.97]               13
    	(858.97, 1007.945]             12
    	(1007.945, 1301.52]            13
    ins_losses:
    	(82.749, 114.645]    13
    	(114.645, 136.05]    13
    	(136.05, 151.87]     12
    	(151.87, 194.78]     13
    abbrev:
    	LA        1
    	MI        1
    	MO        1
    	WY        1
    	Other    47
      DROPPED [] because < 2 vals each.





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
      <th>0</th>
      <td>(18.5, 23.9]</td>
      <td>(6.439, 9.45]</td>
      <td>(5.604, 10.038]</td>
      <td>(16.14, 23.661]</td>
      <td>(13.775, 16.755]</td>
      <td>(768.43, 858.97]</td>
      <td>(136.05, 151.87]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>1</th>
      <td>(15.6, 18.5]</td>
      <td>(6.439, 9.45]</td>
      <td>(3.894, 4.554]</td>
      <td>(16.14, 23.661]</td>
      <td>(16.755, 21.28]</td>
      <td>(1007.945, 1301.52]</td>
      <td>(114.645, 136.05]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>2</th>
      <td>(18.5, 23.9]</td>
      <td>(6.439, 9.45]</td>
      <td>(4.554, 5.604]</td>
      <td>(13.857, 16.14]</td>
      <td>(16.755, 21.28]</td>
      <td>(858.97, 1007.945]</td>
      <td>(82.749, 114.645]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>3</th>
      <td>(18.5, 23.9]</td>
      <td>(3.766, 4.608]</td>
      <td>(5.604, 10.038]</td>
      <td>(16.14, 23.661]</td>
      <td>(16.755, 21.28]</td>
      <td>(768.43, 858.97]</td>
      <td>(136.05, 151.87]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>4</th>
      <td>(5.899, 12.75]</td>
      <td>(3.766, 4.608]</td>
      <td>(1.592, 3.894]</td>
      <td>(10.478, 13.857]</td>
      <td>(5.899, 11.348]</td>
      <td>(858.97, 1007.945]</td>
      <td>(151.87, 194.78]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>5</th>
      <td>(12.75, 15.6]</td>
      <td>(4.608, 6.439]</td>
      <td>(1.592, 3.894]</td>
      <td>(10.478, 13.857]</td>
      <td>(11.348, 13.775]</td>
      <td>(768.43, 858.97]</td>
      <td>(136.05, 151.87]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>6</th>
      <td>(5.899, 12.75]</td>
      <td>(4.608, 6.439]</td>
      <td>(1.592, 3.894]</td>
      <td>(1.7590000000000001, 10.478]</td>
      <td>(5.899, 11.348]</td>
      <td>(1007.945, 1301.52]</td>
      <td>(151.87, 194.78]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>7</th>
      <td>(15.6, 18.5]</td>
      <td>(4.608, 6.439]</td>
      <td>(4.554, 5.604]</td>
      <td>(13.857, 16.14]</td>
      <td>(13.775, 16.755]</td>
      <td>(1007.945, 1301.52]</td>
      <td>(136.05, 151.87]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>8</th>
      <td>(5.899, 12.75]</td>
      <td>(1.7910000000000001, 3.766]</td>
      <td>(1.592, 3.894]</td>
      <td>(1.7590000000000001, 10.478]</td>
      <td>(5.899, 11.348]</td>
      <td>(1007.945, 1301.52]</td>
      <td>(114.645, 136.05]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>9</th>
      <td>(15.6, 18.5]</td>
      <td>(1.7910000000000001, 3.766]</td>
      <td>(4.554, 5.604]</td>
      <td>(16.14, 23.661]</td>
      <td>(16.755, 21.28]</td>
      <td>(1007.945, 1301.52]</td>
      <td>(136.05, 151.87]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>10</th>
      <td>(12.75, 15.6]</td>
      <td>(1.7910000000000001, 3.766]</td>
      <td>(3.894, 4.554]</td>
      <td>(13.857, 16.14]</td>
      <td>(13.775, 16.755]</td>
      <td>(858.97, 1007.945]</td>
      <td>(136.05, 151.87]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>11</th>
      <td>(15.6, 18.5]</td>
      <td>(6.439, 9.45]</td>
      <td>(5.604, 10.038]</td>
      <td>(13.857, 16.14]</td>
      <td>(13.775, 16.755]</td>
      <td>(858.97, 1007.945]</td>
      <td>(114.645, 136.05]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>12</th>
      <td>(12.75, 15.6]</td>
      <td>(4.608, 6.439]</td>
      <td>(3.894, 4.554]</td>
      <td>(10.478, 13.857]</td>
      <td>(13.775, 16.755]</td>
      <td>(641.9590000000001, 768.43]</td>
      <td>(82.749, 114.645]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>13</th>
      <td>(12.75, 15.6]</td>
      <td>(3.766, 4.608]</td>
      <td>(3.894, 4.554]</td>
      <td>(10.478, 13.857]</td>
      <td>(11.348, 13.775]</td>
      <td>(768.43, 858.97]</td>
      <td>(136.05, 151.87]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>14</th>
      <td>(12.75, 15.6]</td>
      <td>(1.7910000000000001, 3.766]</td>
      <td>(3.894, 4.554]</td>
      <td>(10.478, 13.857]</td>
      <td>(11.348, 13.775]</td>
      <td>(641.9590000000001, 768.43]</td>
      <td>(82.749, 114.645]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>15</th>
      <td>(15.6, 18.5]</td>
      <td>(1.7910000000000001, 3.766]</td>
      <td>(3.894, 4.554]</td>
      <td>(13.857, 16.14]</td>
      <td>(11.348, 13.775]</td>
      <td>(641.9590000000001, 768.43]</td>
      <td>(82.749, 114.645]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>16</th>
      <td>(15.6, 18.5]</td>
      <td>(4.608, 6.439]</td>
      <td>(3.894, 4.554]</td>
      <td>(10.478, 13.857]</td>
      <td>(13.775, 16.755]</td>
      <td>(768.43, 858.97]</td>
      <td>(114.645, 136.05]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>17</th>
      <td>(18.5, 23.9]</td>
      <td>(3.766, 4.608]</td>
      <td>(4.554, 5.604]</td>
      <td>(16.14, 23.661]</td>
      <td>(13.775, 16.755]</td>
      <td>(858.97, 1007.945]</td>
      <td>(136.05, 151.87]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>18</th>
      <td>(18.5, 23.9]</td>
      <td>(6.439, 9.45]</td>
      <td>(5.604, 10.038]</td>
      <td>(13.857, 16.14]</td>
      <td>(16.755, 21.28]</td>
      <td>(1007.945, 1301.52]</td>
      <td>(151.87, 194.78]</td>
      <td>LA</td>
    </tr>
    <tr>
      <th>19</th>
      <td>(12.75, 15.6]</td>
      <td>(4.608, 6.439]</td>
      <td>(3.894, 4.554]</td>
      <td>(10.478, 13.857]</td>
      <td>(11.348, 13.775]</td>
      <td>(641.9590000000001, 768.43]</td>
      <td>(82.749, 114.645]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>20</th>
      <td>(5.899, 12.75]</td>
      <td>(3.766, 4.608]</td>
      <td>(3.894, 4.554]</td>
      <td>(1.7590000000000001, 10.478]</td>
      <td>(11.348, 13.775]</td>
      <td>(1007.945, 1301.52]</td>
      <td>(151.87, 194.78]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>21</th>
      <td>(5.899, 12.75]</td>
      <td>(1.7910000000000001, 3.766]</td>
      <td>(1.592, 3.894]</td>
      <td>(1.7590000000000001, 10.478]</td>
      <td>(5.899, 11.348]</td>
      <td>(1007.945, 1301.52]</td>
      <td>(114.645, 136.05]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>22</th>
      <td>(12.75, 15.6]</td>
      <td>(1.7910000000000001, 3.766]</td>
      <td>(3.894, 4.554]</td>
      <td>(10.478, 13.857]</td>
      <td>(5.899, 11.348]</td>
      <td>(1007.945, 1301.52]</td>
      <td>(151.87, 194.78]</td>
      <td>MI</td>
    </tr>
    <tr>
      <th>23</th>
      <td>(5.899, 12.75]</td>
      <td>(1.7910000000000001, 3.766]</td>
      <td>(1.592, 3.894]</td>
      <td>(1.7590000000000001, 10.478]</td>
      <td>(5.899, 11.348]</td>
      <td>(768.43, 858.97]</td>
      <td>(114.645, 136.05]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>24</th>
      <td>(15.6, 18.5]</td>
      <td>(1.7910000000000001, 3.766]</td>
      <td>(4.554, 5.604]</td>
      <td>(1.7590000000000001, 10.478]</td>
      <td>(16.755, 21.28]</td>
      <td>(858.97, 1007.945]</td>
      <td>(151.87, 194.78]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>25</th>
      <td>(15.6, 18.5]</td>
      <td>(6.439, 9.45]</td>
      <td>(4.554, 5.604]</td>
      <td>(13.857, 16.14]</td>
      <td>(11.348, 13.775]</td>
      <td>(768.43, 858.97]</td>
      <td>(136.05, 151.87]</td>
      <td>MO</td>
    </tr>
    <tr>
      <th>26</th>
      <td>(18.5, 23.9]</td>
      <td>(6.439, 9.45]</td>
      <td>(5.604, 10.038]</td>
      <td>(16.14, 23.661]</td>
      <td>(16.755, 21.28]</td>
      <td>(768.43, 858.97]</td>
      <td>(82.749, 114.645]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>27</th>
      <td>(12.75, 15.6]</td>
      <td>(1.7910000000000001, 3.766]</td>
      <td>(4.554, 5.604]</td>
      <td>(10.478, 13.857]</td>
      <td>(11.348, 13.775]</td>
      <td>(641.9590000000001, 768.43]</td>
      <td>(114.645, 136.05]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>28</th>
      <td>(12.75, 15.6]</td>
      <td>(4.608, 6.439]</td>
      <td>(4.554, 5.604]</td>
      <td>(13.857, 16.14]</td>
      <td>(13.775, 16.755]</td>
      <td>(1007.945, 1301.52]</td>
      <td>(136.05, 151.87]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>29</th>
      <td>(5.899, 12.75]</td>
      <td>(3.766, 4.608]</td>
      <td>(1.592, 3.894]</td>
      <td>(1.7590000000000001, 10.478]</td>
      <td>(5.899, 11.348]</td>
      <td>(641.9590000000001, 768.43]</td>
      <td>(114.645, 136.05]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>30</th>
      <td>(5.899, 12.75]</td>
      <td>(1.7910000000000001, 3.766]</td>
      <td>(1.592, 3.894]</td>
      <td>(1.7590000000000001, 10.478]</td>
      <td>(5.899, 11.348]</td>
      <td>(1007.945, 1301.52]</td>
      <td>(151.87, 194.78]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>31</th>
      <td>(15.6, 18.5]</td>
      <td>(1.7910000000000001, 3.766]</td>
      <td>(4.554, 5.604]</td>
      <td>(10.478, 13.857]</td>
      <td>(16.755, 21.28]</td>
      <td>(858.97, 1007.945]</td>
      <td>(114.645, 136.05]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>32</th>
      <td>(5.899, 12.75]</td>
      <td>(3.766, 4.608]</td>
      <td>(1.592, 3.894]</td>
      <td>(10.478, 13.857]</td>
      <td>(5.899, 11.348]</td>
      <td>(1007.945, 1301.52]</td>
      <td>(136.05, 151.87]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>33</th>
      <td>(15.6, 18.5]</td>
      <td>(6.439, 9.45]</td>
      <td>(4.554, 5.604]</td>
      <td>(13.857, 16.14]</td>
      <td>(11.348, 13.775]</td>
      <td>(641.9590000000001, 768.43]</td>
      <td>(114.645, 136.05]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>34</th>
      <td>(18.5, 23.9]</td>
      <td>(4.608, 6.439]</td>
      <td>(5.604, 10.038]</td>
      <td>(16.14, 23.661]</td>
      <td>(16.755, 21.28]</td>
      <td>(641.9590000000001, 768.43]</td>
      <td>(82.749, 114.645]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>35</th>
      <td>(12.75, 15.6]</td>
      <td>(3.766, 4.608]</td>
      <td>(4.554, 5.604]</td>
      <td>(13.857, 16.14]</td>
      <td>(11.348, 13.775]</td>
      <td>(641.9590000000001, 768.43]</td>
      <td>(114.645, 136.05]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>36</th>
      <td>(18.5, 23.9]</td>
      <td>(4.608, 6.439]</td>
      <td>(5.604, 10.038]</td>
      <td>(16.14, 23.661]</td>
      <td>(16.755, 21.28]</td>
      <td>(858.97, 1007.945]</td>
      <td>(151.87, 194.78]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>37</th>
      <td>(12.75, 15.6]</td>
      <td>(3.766, 4.608]</td>
      <td>(1.592, 3.894]</td>
      <td>(1.7590000000000001, 10.478]</td>
      <td>(11.348, 13.775]</td>
      <td>(768.43, 858.97]</td>
      <td>(82.749, 114.645]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>38</th>
      <td>(15.6, 18.5]</td>
      <td>(6.439, 9.45]</td>
      <td>(5.604, 10.038]</td>
      <td>(16.14, 23.661]</td>
      <td>(13.775, 16.755]</td>
      <td>(858.97, 1007.945]</td>
      <td>(151.87, 194.78]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>39</th>
      <td>(5.899, 12.75]</td>
      <td>(3.766, 4.608]</td>
      <td>(3.894, 4.554]</td>
      <td>(1.7590000000000001, 10.478]</td>
      <td>(5.899, 11.348]</td>
      <td>(1007.945, 1301.52]</td>
      <td>(136.05, 151.87]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>40</th>
      <td>(18.5, 23.9]</td>
      <td>(6.439, 9.45]</td>
      <td>(5.604, 10.038]</td>
      <td>(16.14, 23.661]</td>
      <td>(16.755, 21.28]</td>
      <td>(768.43, 858.97]</td>
      <td>(114.645, 136.05]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>41</th>
      <td>(18.5, 23.9]</td>
      <td>(4.608, 6.439]</td>
      <td>(5.604, 10.038]</td>
      <td>(16.14, 23.661]</td>
      <td>(13.775, 16.755]</td>
      <td>(641.9590000000001, 768.43]</td>
      <td>(82.749, 114.645]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>42</th>
      <td>(18.5, 23.9]</td>
      <td>(3.766, 4.608]</td>
      <td>(5.604, 10.038]</td>
      <td>(13.857, 16.14]</td>
      <td>(13.775, 16.755]</td>
      <td>(641.9590000000001, 768.43]</td>
      <td>(151.87, 194.78]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>43</th>
      <td>(18.5, 23.9]</td>
      <td>(6.439, 9.45]</td>
      <td>(5.604, 10.038]</td>
      <td>(16.14, 23.661]</td>
      <td>(16.755, 21.28]</td>
      <td>(858.97, 1007.945]</td>
      <td>(151.87, 194.78]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>44</th>
      <td>(5.899, 12.75]</td>
      <td>(4.608, 6.439]</td>
      <td>(1.592, 3.894]</td>
      <td>(1.7590000000000001, 10.478]</td>
      <td>(5.899, 11.348]</td>
      <td>(768.43, 858.97]</td>
      <td>(82.749, 114.645]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>45</th>
      <td>(12.75, 15.6]</td>
      <td>(3.766, 4.608]</td>
      <td>(3.894, 4.554]</td>
      <td>(10.478, 13.857]</td>
      <td>(11.348, 13.775]</td>
      <td>(641.9590000000001, 768.43]</td>
      <td>(82.749, 114.645]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>46</th>
      <td>(5.899, 12.75]</td>
      <td>(1.7910000000000001, 3.766]</td>
      <td>(1.592, 3.894]</td>
      <td>(10.478, 13.857]</td>
      <td>(5.899, 11.348]</td>
      <td>(768.43, 858.97]</td>
      <td>(151.87, 194.78]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>47</th>
      <td>(5.899, 12.75]</td>
      <td>(3.766, 4.608]</td>
      <td>(1.592, 3.894]</td>
      <td>(1.7590000000000001, 10.478]</td>
      <td>(5.899, 11.348]</td>
      <td>(858.97, 1007.945]</td>
      <td>(82.749, 114.645]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>48</th>
      <td>(18.5, 23.9]</td>
      <td>(6.439, 9.45]</td>
      <td>(5.604, 10.038]</td>
      <td>(16.14, 23.661]</td>
      <td>(16.755, 21.28]</td>
      <td>(858.97, 1007.945]</td>
      <td>(151.87, 194.78]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>49</th>
      <td>(12.75, 15.6]</td>
      <td>(4.608, 6.439]</td>
      <td>(3.894, 4.554]</td>
      <td>(1.7590000000000001, 10.478]</td>
      <td>(11.348, 13.775]</td>
      <td>(641.9590000000001, 768.43]</td>
      <td>(82.749, 114.645]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>50</th>
      <td>(15.6, 18.5]</td>
      <td>(6.439, 9.45]</td>
      <td>(4.554, 5.604]</td>
      <td>(13.857, 16.14]</td>
      <td>(13.775, 16.755]</td>
      <td>(768.43, 858.97]</td>
      <td>(114.645, 136.05]</td>
      <td>WY</td>
    </tr>
  </tbody>
</table>
</div>


