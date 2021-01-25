# Machine Learning Pipelines

## Scikit-Learn Pipeline

https://scikit-learn.org/stable/modules/generated/sklearn.pipeline.Pipeline.html

```python3
from sklearn.pipeline import Pipeline

# ('name_of_the_object', initialization)
pipeline = Pipeline([('vect', CountVectorizer()),
                     ('tfidf', TfidfTransformer()),
                     ('clf', RandomForestClassifier())])
                     
pipeline.fit(X_train, y_train)

y_pred = pipeline.predict(X_test) # the last object in the pipeline is a classifier, which has the predict method

```

## Scikit-Learn Feature Union

```python3
from sklearn.pipeline import Pipeline, FeatureUnion

pipeline = Pipeline([('features', FeatureUnion([('nlp_pipeline', Pipeline([('vect', CountVectorizer()),
                                                                           ('tfidf', TfidfTransformer())]),
                                                 ('txt_len', TextLengthExtractor())]),
                     ('clf', RandomForestClassifier())])
                     
pipeline.fit(X_train, y_train)

y_pred = pipeline.predict(X_test) # the last object in the pipeline is a classifier, which has the predict method

```

## Creating Custom Transformers

Custom transforms need `.fit()` and `.transform()` methods

```python3
from sklearn.base import BaseEstimator, TransformerMixin

class CaseNormalizer(BaseEstimator, TransformerMixin):
    def __init__(self):
        pass
    
    def fit(self, X, y = None):
        return self
    
    def transform(self, X):
        return pd.Series(X).apply(lambda x: x.lower()).values
        
custom_transformer = CaseNormalizer()
```

## Convert Existing Function into Transformers

Use `sklearn.preprocessing.FunctionTransformer`

```python3
import numpy as np
from sklearn.preprocessing inport FunctionTransformer

transformer = FunctionTransformer(np.log1p)
```


## Gridsearch

Method of tuning hyperparameters throughout data preprocessing and model by using cross-validation

Define a diction with key = name_of_the_parameter, and value = list_of_values_to_validate

`sklearn.model_selection.GridSearchCV` https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.GridSearchCV.html

```python3
from sklearn.model_selection import GridSearchCV

pipeline = Pipeline([('Scaler', StandardScaler()),
                     ('clf', RandomForestClassifier())])

hyperparameters_dict = {'clf__criterion': ['gini', 'entropy'],
                        'clf__max_features': ['auto', 'sqrt', 'log2']}
                   
cv = GridSearchCV(pipeline, param_grid = hyperparameters_dict)
cv.fit(X_train, y_train)

y_pred = cv.predict(X_test)
```

To determine which parameters are there in the pipeline, use `pipeline.get_params()` or `pipeline.get_params().keys()`
