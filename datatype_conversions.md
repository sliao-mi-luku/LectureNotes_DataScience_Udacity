# Conversion of datatypes in Pandas


A practical way is to read the dataset assuming all columns are strings by setting `dtype = str`. After the data is loaded, \
values of different columns can be converted to the corresponding data types.


``` python3
import pandas as pd

df = pd.read_csv("dataset.csv", dtype = str)
```


`pd.to_numeric` converts the data into a numeric type
`pd.to_datetime`
`pd.to_timedelta`
