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

pipeline.predict(X_test)

```