# Encodings

The default of encoding by Pandas is utf-8. When handling a dataset with unknown encoding other than utf-8, an *UnicodeDecodeError* occurs.

To solve this, simply test every possible encodings supported by Python [list here](https://docs.python.org/3/library/codecs.html#standard-encodings)

All supported encoding methods can be iterated over by the built-in dictionary `encodings.aliases`

```python3
from encoding.aliases import aliases

alias_candidates = set(aliases.values())

for candidate in alias_candidates:
    try:
        pd.read_csv('csv_file_with_unknown_encoding.csv', encode = candidate)
        print("Encoding is {}".format(candidate))
    except:
        pass
```

## chardet library

```python3
import chardet

with open('csv_file_with_unknown_encoding.csv', 'rb') as f:
    print(chardet.detect(f.read()))
```
