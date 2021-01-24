# NLP Pipelines


## Fetching data from a website

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

``python3
import re

texts = re.sub(r"[^a-zA-Z0-9]", " ", text)
```


