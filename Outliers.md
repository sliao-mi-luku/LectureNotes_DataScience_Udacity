# Outliers


## Outlier Detection

https://scikit-learn.org/stable/modules/outlier_detection.html

https://towardsdatascience.com/a-brief-overview-of-outlier-detection-techniques-1e0b2c19e561


**Tukey rule**

Tukey rule finds outliers in 1-dimension. Given a 1-dimensional data, we calculate the first quartile (Q1) and the third quartile (Q3)

`interquartile range = IQR = Q3 - Q1`

`max_value = Q3 + 1.5*IQR`

`min_value = Q1 - 1.5*IQR`

Data greater than *max_value* or smaller than *min_value* are identified as outliers.
