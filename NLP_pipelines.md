# NLP Pipelines


## Text Preprocessing

### Use `requests` to get website data

```python3
import requests

r = requests.get('WEB_PAGE_URL')

# print out the texts
print(r.text)
```

### Use `BeautifulSoup` to remove HTML tags

```python3
from bs4 import BeautifulSoup

soup = BeautifulSoup(r.text, "html5lib") ## or use "lxml"
```

### Use `re` to find all URLs

The regular expression for URL

```python3
import re

URL_REGEX = 'http[s]?://(?:[a-zA-Z]|[0-9]|[$-_@.&+]|[!*\(\),]|(?:%[0-9a-fA-F][0-9a-fA-F]))+'

detected_urls = re.findall(URL_REGEX, text) # returns a list of matched strings

```

### Use `BeautifulSoup` to extract 

```python3
texts = soup.find_all("div", {"class": "the-class-name"})

print(texts[0].prettify()) # prints out the first item

texts[0].select_one("h3 a").get_texts().strip()

texts[0].select_one("div[the-attribute-name]")
```

### Case normalization

```python3
texts = texts.lower()
```

### Remove punctuations

```python3
import re

texts = re.sub(r"[^a-zA-Z0-9]", " ", text)
```

### Tokenization

```python3
from nltk.tokenize import word_tokenize

words = word_tokenize(text)
```

### Sentence Tokenization

```python3
from nltk.tokenize import sent_tokenize

sentences = sent_tokenize(text) # splits a paragraph into a list of sentences
```

### Stop Word Removal

```python3
# List all stop words in English
from nltk.corpus import stopwords

print(stopwords.words("english"))
```

### Part-of-Speech Tagging

```python3
from nltk import pos_tag
from nltk.tokenize import word_tokenize

pos_tag(word_tokenize("This is a pan."))
```
### Named Entity Recognition

```python3
from nltk import pos_tag, ne_chunk
from nltk.tokenize import word_tokenize

ne_chunk(pos_tag(word_tokenize("This is a pan.")))
```

### Stemming & Lemmatization

**Porter Stemmer**

```python3
from nltk.stem.porter import PorterStemmer

stemmed = [PorterStemmer().stem(w) for w in words] # words is a list of strings of words
```

**Lemmatization**

```python3
from nltk.stem.wordnet import WordNetLemmatizer

# transform nouns (default)
lemmed = [WordNetLemmatizer().lemmatize(w) for w in words] # words is a list of strings of words

# transform verbs
lemmed = [WordNetLemmatizer().lemmatize(w, pos = 'v') for w in lemmed]
```

### Feature Extraction

**Bag of Words**

``` python3
import re
from nltk.corpus import stopwords
from nltk.tokenize import word_tokenize
from nltk.stem.wordnet import WordNetLemmatizer
from sklearn.feature_extraction.text import CountVectorizer

STOPWORDS = stopwords.words("english")

lemmatizer = WordNetLemmatizer()


def tokenize(text):
  text = re.sub(r"[^a-zA-Z0-9]", " ", text.lower())
  tokens = word_tokenize(text)
  tokens = [lemmatizer.lemmatize(w) for w in tokens if w not in STOPWORDS]
  return tokens

vect = CountVectorizer(tokenizer = tokenize) # func tokenizer will process each element (a sentence) of copos

x = vect.fit_transform(corpus) # corpus is a list of sentences

x.toarray() # view x

vect.vocabulary_ # view token vocabulary and counts

```

**TF-IDF**

`TF` (term frequency)

td(t, d) = count(t, d) / |d|

`IDF` (inverse document frequency)

idf(t, D) = log(|D| / |{all d that contain t}|)

`tfidf(t, d, D) = td(t, d) x idf(t, D)`

```python3
from sklearn.feature_extraction.text import TfidfTransformer

tfidf_transformer = TfidfTransformer(smooth_idf = False)

tfidf = tfidf_transformer.fit_transform(x)

tfidf.toarray()
```

**Bag-of-words + TF-IDF**

```python3
from sklearn.feature_extraction.text import TfidfVectorizer

vectorizer = TfidfVectorizer()

x = vectorizer.fit_transform(corpus) # corpus is a list of sentences (str)

x.toarray()
```

**One-Hot Encoding**



**Word Embeddings**


**Word2Vec**

Given neighbors predict the middle word -> Countinuous Bag of Words

Given the middle word predict neighbors -> Continuous Skip-gram

**Glove**



**Embeddings for Deep Learning**

**t-SNE**

t-Distributed Stochastic Neighbor Embedding










