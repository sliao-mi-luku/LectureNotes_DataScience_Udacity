# Filling in Missing Values

Suppose we have a dataframe (df) with columns `Country`, `Year`, `GDP`. Some `GDP` values are missing 

### Method 1: Using mean values of the same group

```python3
"""
Create a new column 'GDP_mean_filled' by filling in mean GDP for each country
"""

df['GDP_mean_filled'] = df.groupby('Country')['GDP'].transform(lambda x: x.fillna(x.mean()))

```

### Method 2: Forward and backward filling

```python3
"""
Create a new column 'GDP_forward_backward_filled' by forward filling followed by a backward filling.
Use both direction filling ensures that we can fill in missing data on both ends.
"""

df['GDP_forward_backward_filled'] = df.sort_values('Year').groupby('Country')['GDP'].fillna(method = 'ffill').fillna(method = 'bfill')
```
