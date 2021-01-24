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

**TF-IDF**

`TF` (term frequency)

td(t, d) = count(t, d) / |d|

`IDF` (inverse document frequency)

idf(t, D) = log(|D| / |{all d that contain t}|)

**tfidf(t, d, D) = td(t, d) x idf(t, D)**


















