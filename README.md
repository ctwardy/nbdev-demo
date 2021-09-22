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
      <th>1</th>
      <td>18.1</td>
      <td>7.421</td>
      <td>4.525</td>
      <td>16.290</td>
      <td>17.014</td>
      <td>1053.48</td>
      <td>133.93</td>
      <td>AK</td>
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
      <th>24</th>
      <td>17.6</td>
      <td>2.640</td>
      <td>5.456</td>
      <td>1.760</td>
      <td>17.600</td>
      <td>896.07</td>
      <td>155.77</td>
      <td>MS</td>
    </tr>
    <tr>
      <th>31</th>
      <td>18.4</td>
      <td>3.496</td>
      <td>4.968</td>
      <td>12.328</td>
      <td>18.032</td>
      <td>869.85</td>
      <td>120.75</td>
      <td>NM</td>
    </tr>
    <tr>
      <th>29</th>
      <td>11.6</td>
      <td>4.060</td>
      <td>3.480</td>
      <td>10.092</td>
      <td>9.628</td>
      <td>746.54</td>
      <td>120.21</td>
      <td>NH</td>
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

    total:
    	(5.899, 11.1]    6
    	(11.1, 12.3]     5
    	(12.3, 13.6]     6
    	(13.6, 14.5]     4
    	(14.5, 15.6]     5
    	(15.6, 17.4]     5
    	(17.4, 18.1]     5
    	(18.1, 19.4]     6
    	(19.4, 21.4]     5
    	(21.4, 23.9]     4
    speeding:
    	(1.7910000000000001, 2.413]    6
    	(2.413, 3.496]                 5
    	(3.496, 3.948]                 5
    	(3.948, 4.095]                 5
    	(4.095, 4.608]                 5
    	(4.608, 5.032]                 5
    	(5.032, 6.014]                 5
    	(6.014, 6.923]                 5
    	(6.923, 7.76]                  5
    	(7.76, 9.45]                   5
    alcohol:
    	(1.592, 3.328]     6
    	(3.328, 3.567]     5
    	(3.567, 3.948]     5
    	(3.948, 4.272]     5
    	(4.272, 4.554]     5
    	(4.554, 4.968]     5
    	(4.968, 5.456]     5
    	(5.456, 5.655]     5
    	(5.655, 6.765]     5
    	(6.765, 10.038]    5
    not_distracted:
    	(1.7590000000000001, 8.576]    6
    	(8.576, 9.944]                 5
    	(9.944, 10.92]                 5
    	(10.92, 13.056]                5
    	(13.056, 13.857]               5
    	(13.857, 14.35]                5
    	(14.35, 15.624]                5
    	(15.624, 16.692]               5
    	(16.692, 18.308]               5
    	(18.308, 23.661]               5
    no_previous:
    	(5.899, 8.856]      6
    	(8.856, 10.848]     5
    	(10.848, 11.592]    5
    	(11.592, 12.92]     5
    	(12.92, 13.775]     5
    	(13.775, 15.13]     5
    	(15.13, 16.038]     5
    	(16.038, 17.014]    5
    	(17.014, 18.706]    5
    	(18.706, 21.28]     5
    ins_premium:
    	(641.9590000000001, 688.75]    6
    	(688.75, 732.28]               5
    	(732.28, 780.45]               5
    	(780.45, 804.71]               5
    	(804.71, 858.97]               5
    	(858.97, 881.51]               5
    	(881.51, 913.15]               5
    	(913.15, 1048.78]              5
    	(1048.78, 1148.99]             5
    	(1148.99, 1301.52]             5
    ins_losses:
    	(82.749, 106.62]    6
    	(106.62, 110.35]    5
    	(110.35, 120.21]    5
    	(120.21, 133.35]    5
    	(133.35, 136.05]    5
    	(136.05, 142.39]    5
    	(142.39, 148.58]    5
    	(148.58, 153.72]    5
    	(153.72, 159.85]    5
    	(159.85, 194.78]    5
    abbrev:
    	AR        1
    	FL        1
    	IA        1
    	IL        1
    	MD        1
    	MN        1
    	NM        1
    	NY        1
    	WA        1
    	WV        1
    	Other    41
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
      <td>(18.1, 19.4]</td>
      <td>(6.923, 7.76]</td>
      <td>(5.456, 5.655]</td>
      <td>(16.692, 18.308]</td>
      <td>(13.775, 15.13]</td>
      <td>(780.45, 804.71]</td>
      <td>(142.39, 148.58]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>1</th>
      <td>(17.4, 18.1]</td>
      <td>(6.923, 7.76]</td>
      <td>(4.272, 4.554]</td>
      <td>(15.624, 16.692]</td>
      <td>(16.038, 17.014]</td>
      <td>(1048.78, 1148.99]</td>
      <td>(133.35, 136.05]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>2</th>
      <td>(18.1, 19.4]</td>
      <td>(6.014, 6.923]</td>
      <td>(4.968, 5.456]</td>
      <td>(14.35, 15.624]</td>
      <td>(17.014, 18.706]</td>
      <td>(881.51, 913.15]</td>
      <td>(106.62, 110.35]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>3</th>
      <td>(21.4, 23.9]</td>
      <td>(3.948, 4.095]</td>
      <td>(5.655, 6.765]</td>
      <td>(18.308, 23.661]</td>
      <td>(18.706, 21.28]</td>
      <td>(804.71, 858.97]</td>
      <td>(136.05, 142.39]</td>
      <td>AR</td>
    </tr>
    <tr>
      <th>4</th>
      <td>(11.1, 12.3]</td>
      <td>(4.095, 4.608]</td>
      <td>(3.328, 3.567]</td>
      <td>(9.944, 10.92]</td>
      <td>(8.856, 10.848]</td>
      <td>(858.97, 881.51]</td>
      <td>(159.85, 194.78]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>5</th>
      <td>(12.3, 13.6]</td>
      <td>(4.608, 5.032]</td>
      <td>(3.567, 3.948]</td>
      <td>(9.944, 10.92]</td>
      <td>(11.592, 12.92]</td>
      <td>(804.71, 858.97]</td>
      <td>(136.05, 142.39]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>6</th>
      <td>(5.899, 11.1]</td>
      <td>(4.608, 5.032]</td>
      <td>(3.567, 3.948]</td>
      <td>(8.576, 9.944]</td>
      <td>(5.899, 8.856]</td>
      <td>(1048.78, 1148.99]</td>
      <td>(159.85, 194.78]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>7</th>
      <td>(15.6, 17.4]</td>
      <td>(6.014, 6.923]</td>
      <td>(4.554, 4.968]</td>
      <td>(13.857, 14.35]</td>
      <td>(15.13, 16.038]</td>
      <td>(1048.78, 1148.99]</td>
      <td>(148.58, 153.72]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>8</th>
      <td>(5.899, 11.1]</td>
      <td>(1.7910000000000001, 2.413]</td>
      <td>(1.592, 3.328]</td>
      <td>(1.7590000000000001, 8.576]</td>
      <td>(5.899, 8.856]</td>
      <td>(1148.99, 1301.52]</td>
      <td>(133.35, 136.05]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>9</th>
      <td>(17.4, 18.1]</td>
      <td>(3.496, 3.948]</td>
      <td>(4.968, 5.456]</td>
      <td>(15.624, 16.692]</td>
      <td>(16.038, 17.014]</td>
      <td>(1148.99, 1301.52]</td>
      <td>(142.39, 148.58]</td>
      <td>FL</td>
    </tr>
    <tr>
      <th>10</th>
      <td>(14.5, 15.6]</td>
      <td>(2.413, 3.496]</td>
      <td>(3.567, 3.948]</td>
      <td>(14.35, 15.624]</td>
      <td>(13.775, 15.13]</td>
      <td>(881.51, 913.15]</td>
      <td>(142.39, 148.58]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>11</th>
      <td>(17.4, 18.1]</td>
      <td>(7.76, 9.45]</td>
      <td>(6.765, 10.038]</td>
      <td>(13.857, 14.35]</td>
      <td>(15.13, 16.038]</td>
      <td>(858.97, 881.51]</td>
      <td>(120.21, 133.35]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>12</th>
      <td>(14.5, 15.6]</td>
      <td>(5.032, 6.014]</td>
      <td>(4.272, 4.554]</td>
      <td>(10.92, 13.056]</td>
      <td>(13.775, 15.13]</td>
      <td>(641.9590000000001, 688.75]</td>
      <td>(82.749, 106.62]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>13</th>
      <td>(12.3, 13.6]</td>
      <td>(4.095, 4.608]</td>
      <td>(4.272, 4.554]</td>
      <td>(10.92, 13.056]</td>
      <td>(11.592, 12.92]</td>
      <td>(780.45, 804.71]</td>
      <td>(136.05, 142.39]</td>
      <td>IL</td>
    </tr>
    <tr>
      <th>14</th>
      <td>(13.6, 14.5]</td>
      <td>(3.496, 3.948]</td>
      <td>(3.948, 4.272]</td>
      <td>(13.056, 13.857]</td>
      <td>(12.92, 13.775]</td>
      <td>(688.75, 732.28]</td>
      <td>(106.62, 110.35]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>15</th>
      <td>(15.6, 17.4]</td>
      <td>(2.413, 3.496]</td>
      <td>(3.567, 3.948]</td>
      <td>(14.35, 15.624]</td>
      <td>(12.92, 13.775]</td>
      <td>(641.9590000000001, 688.75]</td>
      <td>(110.35, 120.21]</td>
      <td>IA</td>
    </tr>
    <tr>
      <th>16</th>
      <td>(17.4, 18.1]</td>
      <td>(4.608, 5.032]</td>
      <td>(3.948, 4.272]</td>
      <td>(13.056, 13.857]</td>
      <td>(13.775, 15.13]</td>
      <td>(732.28, 780.45]</td>
      <td>(133.35, 136.05]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>17</th>
      <td>(19.4, 21.4]</td>
      <td>(3.948, 4.095]</td>
      <td>(4.554, 4.968]</td>
      <td>(15.624, 16.692]</td>
      <td>(16.038, 17.014]</td>
      <td>(858.97, 881.51]</td>
      <td>(136.05, 142.39]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>18</th>
      <td>(19.4, 21.4]</td>
      <td>(6.923, 7.76]</td>
      <td>(5.655, 6.765]</td>
      <td>(14.35, 15.624]</td>
      <td>(18.706, 21.28]</td>
      <td>(1148.99, 1301.52]</td>
      <td>(159.85, 194.78]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>19</th>
      <td>(14.5, 15.6]</td>
      <td>(5.032, 6.014]</td>
      <td>(4.272, 4.554]</td>
      <td>(13.056, 13.857]</td>
      <td>(11.592, 12.92]</td>
      <td>(641.9590000000001, 688.75]</td>
      <td>(82.749, 106.62]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>20</th>
      <td>(12.3, 13.6]</td>
      <td>(4.095, 4.608]</td>
      <td>(3.948, 4.272]</td>
      <td>(8.576, 9.944]</td>
      <td>(11.592, 12.92]</td>
      <td>(913.15, 1048.78]</td>
      <td>(159.85, 194.78]</td>
      <td>MD</td>
    </tr>
    <tr>
      <th>21</th>
      <td>(5.899, 11.1]</td>
      <td>(1.7910000000000001, 2.413]</td>
      <td>(1.592, 3.328]</td>
      <td>(1.7590000000000001, 8.576]</td>
      <td>(5.899, 8.856]</td>
      <td>(913.15, 1048.78]</td>
      <td>(133.35, 136.05]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>22</th>
      <td>(13.6, 14.5]</td>
      <td>(2.413, 3.496]</td>
      <td>(3.567, 3.948]</td>
      <td>(13.056, 13.857]</td>
      <td>(10.848, 11.592]</td>
      <td>(1048.78, 1148.99]</td>
      <td>(148.58, 153.72]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>23</th>
      <td>(5.899, 11.1]</td>
      <td>(1.7910000000000001, 2.413]</td>
      <td>(1.592, 3.328]</td>
      <td>(1.7590000000000001, 8.576]</td>
      <td>(5.899, 8.856]</td>
      <td>(732.28, 780.45]</td>
      <td>(120.21, 133.35]</td>
      <td>MN</td>
    </tr>
    <tr>
      <th>24</th>
      <td>(17.4, 18.1]</td>
      <td>(2.413, 3.496]</td>
      <td>(4.968, 5.456]</td>
      <td>(1.7590000000000001, 8.576]</td>
      <td>(17.014, 18.706]</td>
      <td>(881.51, 913.15]</td>
      <td>(153.72, 159.85]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>25</th>
      <td>(15.6, 17.4]</td>
      <td>(6.014, 6.923]</td>
      <td>(5.456, 5.655]</td>
      <td>(14.35, 15.624]</td>
      <td>(12.92, 13.775]</td>
      <td>(780.45, 804.71]</td>
      <td>(142.39, 148.58]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>26</th>
      <td>(19.4, 21.4]</td>
      <td>(7.76, 9.45]</td>
      <td>(6.765, 10.038]</td>
      <td>(16.692, 18.308]</td>
      <td>(17.014, 18.706]</td>
      <td>(804.71, 858.97]</td>
      <td>(82.749, 106.62]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>27</th>
      <td>(14.5, 15.6]</td>
      <td>(1.7910000000000001, 2.413]</td>
      <td>(4.968, 5.456]</td>
      <td>(13.056, 13.857]</td>
      <td>(12.92, 13.775]</td>
      <td>(688.75, 732.28]</td>
      <td>(110.35, 120.21]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>28</th>
      <td>(14.5, 15.6]</td>
      <td>(5.032, 6.014]</td>
      <td>(4.554, 4.968]</td>
      <td>(13.857, 14.35]</td>
      <td>(13.775, 15.13]</td>
      <td>(913.15, 1048.78]</td>
      <td>(136.05, 142.39]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>29</th>
      <td>(11.1, 12.3]</td>
      <td>(3.948, 4.095]</td>
      <td>(3.328, 3.567]</td>
      <td>(9.944, 10.92]</td>
      <td>(8.856, 10.848]</td>
      <td>(732.28, 780.45]</td>
      <td>(110.35, 120.21]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>30</th>
      <td>(11.1, 12.3]</td>
      <td>(1.7910000000000001, 2.413]</td>
      <td>(1.592, 3.328]</td>
      <td>(8.576, 9.944]</td>
      <td>(5.899, 8.856]</td>
      <td>(1148.99, 1301.52]</td>
      <td>(153.72, 159.85]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>31</th>
      <td>(18.1, 19.4]</td>
      <td>(2.413, 3.496]</td>
      <td>(4.554, 4.968]</td>
      <td>(10.92, 13.056]</td>
      <td>(17.014, 18.706]</td>
      <td>(858.97, 881.51]</td>
      <td>(120.21, 133.35]</td>
      <td>NM</td>
    </tr>
    <tr>
      <th>32</th>
      <td>(11.1, 12.3]</td>
      <td>(3.496, 3.948]</td>
      <td>(3.328, 3.567]</td>
      <td>(9.944, 10.92]</td>
      <td>(8.856, 10.848]</td>
      <td>(1148.99, 1301.52]</td>
      <td>(148.58, 153.72]</td>
      <td>NY</td>
    </tr>
    <tr>
      <th>33</th>
      <td>(15.6, 17.4]</td>
      <td>(6.014, 6.923]</td>
      <td>(4.968, 5.456]</td>
      <td>(15.624, 16.692]</td>
      <td>(12.92, 13.775]</td>
      <td>(688.75, 732.28]</td>
      <td>(120.21, 133.35]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>34</th>
      <td>(21.4, 23.9]</td>
      <td>(5.032, 6.014]</td>
      <td>(6.765, 10.038]</td>
      <td>(18.308, 23.661]</td>
      <td>(18.706, 21.28]</td>
      <td>(641.9590000000001, 688.75]</td>
      <td>(106.62, 110.35]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>35</th>
      <td>(13.6, 14.5]</td>
      <td>(3.496, 3.948]</td>
      <td>(4.554, 4.968]</td>
      <td>(13.857, 14.35]</td>
      <td>(10.848, 11.592]</td>
      <td>(688.75, 732.28]</td>
      <td>(133.35, 136.05]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>36</th>
      <td>(19.4, 21.4]</td>
      <td>(6.014, 6.923]</td>
      <td>(5.655, 6.765]</td>
      <td>(16.692, 18.308]</td>
      <td>(17.014, 18.706]</td>
      <td>(858.97, 881.51]</td>
      <td>(159.85, 194.78]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>37</th>
      <td>(12.3, 13.6]</td>
      <td>(4.095, 4.608]</td>
      <td>(1.592, 3.328]</td>
      <td>(1.7590000000000001, 8.576]</td>
      <td>(10.848, 11.592]</td>
      <td>(780.45, 804.71]</td>
      <td>(82.749, 106.62]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>38</th>
      <td>(18.1, 19.4]</td>
      <td>(7.76, 9.45]</td>
      <td>(5.456, 5.655]</td>
      <td>(16.692, 18.308]</td>
      <td>(15.13, 16.038]</td>
      <td>(881.51, 913.15]</td>
      <td>(153.72, 159.85]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>39</th>
      <td>(5.899, 11.1]</td>
      <td>(3.496, 3.948]</td>
      <td>(3.948, 4.272]</td>
      <td>(9.944, 10.92]</td>
      <td>(5.899, 8.856]</td>
      <td>(1048.78, 1148.99]</td>
      <td>(142.39, 148.58]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>40</th>
      <td>(21.4, 23.9]</td>
      <td>(7.76, 9.45]</td>
      <td>(6.765, 10.038]</td>
      <td>(18.308, 23.661]</td>
      <td>(18.706, 21.28]</td>
      <td>(804.71, 858.97]</td>
      <td>(110.35, 120.21]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>41</th>
      <td>(18.1, 19.4]</td>
      <td>(5.032, 6.014]</td>
      <td>(5.655, 6.765]</td>
      <td>(18.308, 23.661]</td>
      <td>(16.038, 17.014]</td>
      <td>(641.9590000000001, 688.75]</td>
      <td>(82.749, 106.62]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>42</th>
      <td>(19.4, 21.4]</td>
      <td>(3.948, 4.095]</td>
      <td>(5.456, 5.655]</td>
      <td>(15.624, 16.692]</td>
      <td>(15.13, 16.038]</td>
      <td>(732.28, 780.45]</td>
      <td>(153.72, 159.85]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>43</th>
      <td>(18.1, 19.4]</td>
      <td>(6.923, 7.76]</td>
      <td>(6.765, 10.038]</td>
      <td>(16.692, 18.308]</td>
      <td>(16.038, 17.014]</td>
      <td>(913.15, 1048.78]</td>
      <td>(153.72, 159.85]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>44</th>
      <td>(11.1, 12.3]</td>
      <td>(4.608, 5.032]</td>
      <td>(1.592, 3.328]</td>
      <td>(8.576, 9.944]</td>
      <td>(8.856, 10.848]</td>
      <td>(804.71, 858.97]</td>
      <td>(106.62, 110.35]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>45</th>
      <td>(12.3, 13.6]</td>
      <td>(3.948, 4.095]</td>
      <td>(3.948, 4.272]</td>
      <td>(10.92, 13.056]</td>
      <td>(11.592, 12.92]</td>
      <td>(688.75, 732.28]</td>
      <td>(106.62, 110.35]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>46</th>
      <td>(12.3, 13.6]</td>
      <td>(1.7910000000000001, 2.413]</td>
      <td>(3.328, 3.567]</td>
      <td>(10.92, 13.056]</td>
      <td>(10.848, 11.592]</td>
      <td>(732.28, 780.45]</td>
      <td>(148.58, 153.72]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>47</th>
      <td>(5.899, 11.1]</td>
      <td>(4.095, 4.608]</td>
      <td>(3.328, 3.567]</td>
      <td>(8.576, 9.944]</td>
      <td>(8.856, 10.848]</td>
      <td>(881.51, 913.15]</td>
      <td>(110.35, 120.21]</td>
      <td>WA</td>
    </tr>
    <tr>
      <th>48</th>
      <td>(21.4, 23.9]</td>
      <td>(7.76, 9.45]</td>
      <td>(5.655, 6.765]</td>
      <td>(18.308, 23.661]</td>
      <td>(18.706, 21.28]</td>
      <td>(913.15, 1048.78]</td>
      <td>(148.58, 153.72]</td>
      <td>WV</td>
    </tr>
    <tr>
      <th>49</th>
      <td>(13.6, 14.5]</td>
      <td>(4.608, 5.032]</td>
      <td>(4.272, 4.554]</td>
      <td>(1.7590000000000001, 8.576]</td>
      <td>(10.848, 11.592]</td>
      <td>(641.9590000000001, 688.75]</td>
      <td>(82.749, 106.62]</td>
      <td>Other</td>
    </tr>
    <tr>
      <th>50</th>
      <td>(15.6, 17.4]</td>
      <td>(6.923, 7.76]</td>
      <td>(5.456, 5.655]</td>
      <td>(13.857, 14.35]</td>
      <td>(15.13, 16.038]</td>
      <td>(780.45, 804.71]</td>
      <td>(120.21, 133.35]</td>
      <td>Other</td>
    </tr>
  </tbody>
</table>
</div>


