# Load

Loading data is the 3rd steps in the ETL pipelines.

---
Given a dataframe `df`

`df.to_csv('data.csv', index = False)` outputs the dataframe as a CSV file (without saving indexes)

`df.to_json('data.json', orient = 'records')` outputs the dataframe as a JSON file

The codes below output the dataframe as a salite database file

```python3
import sqlite3
conn = sqlite3.connect('database.db')
df.to_sql('df', con = conn, if_exists = 'replace')
```
