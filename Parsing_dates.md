# Parsing Dates


`pd.to_datetime` can help parsing the date

``` python3
import pandas as pd

parsed_date = pd.to_datetime('July 10, 1999') # which will return Timestamp('1999-07-10 00:00:00')
```

You can look up the year, month, or the second of `parsed_date`

``` python3
parsed_date.month # witch will return 1
```

The defualt format of pandas is **Day/Month/Year**. You can sepcify the format by setting the argument `format`

```python3
parsed_date = pd.to_datetime("01/03/2000", format = "%m%d%Y")
```

**Datetimde codes** [look-up table](https://strftime.org/)

## pd.Series.dt

`pd.Series.dt` [documentation](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.Series.dt.html)

By using pd.Series.dt, we can treat the Series values as datetimes and access detailed information such as

```python3
df['date'].dt.second # returns the second value
df['date'].dt.month # returns the month (1 to 12)
df['date'].dt.weekdat # returns an integer (0:Monday, ..., 6:Sunday)
```
