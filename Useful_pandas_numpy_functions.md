# Useful pandas/numpy functions

Below lists several useful methods used in the study of data science.


## Pandas
---
`Series.replace`/`DataFrame.replace` can replace texts. Ex. `df['col'].replace(REGULAR_EXPRESSION, regex = True)`

[Regex Cheatsheet](https://medium.com/factory-mind/regex-tutorial-a-simple-cheatsheet-by-examples-649dc1c3f285)
[Regex Cookbook](https://medium.com/factory-mind/regex-cookbook-most-wanted-regex-aa721558c3c1)

---
`pad.get_dummies()` can create dummy variables for categorical data. Ex. 





## Numpy
---

Count the number of duplicates in an ndarry

`items, counts = np.unique(ndarray, return_counts = True)` 
