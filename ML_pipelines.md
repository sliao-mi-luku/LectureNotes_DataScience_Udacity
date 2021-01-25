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
from sklearn.pipeline import Pipeline

pipeline = Pipeline([('features', FeatureUnion([('nlp_pipeline', Pipeline([('vect', CountVectorizer()),
                                                                           ('tfidf', TfidfTransformer())]),
                                                 ('txt_len', TextLengthExtractor())]),
                     ('clf', RandomForestClassifier())])
                     
pipeline.fit(X_train, y_train)

y_pred = pipeline.predict(X_test) # the last object in the pipeline is a classifier, which has the predict method

```


## Gridsearch

Method of tuning hyperparameters throughout data preprocessing and model

```python3

```
