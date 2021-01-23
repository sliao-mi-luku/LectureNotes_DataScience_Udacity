# Extract SQL Data

## sqlite3

The library **sqlite3** can be used to extract SQL data:

1. connect to the data base by `conn = sqlite3.connect(*name_of_database*)`
2. send a query to get the corresponding dataframe by `pd.read_sql(*SQL_query*, conn)`

```python3
import sqlite3
import pandas as pd

conn = sqlite3.connect("database.db")
df = pd.read_sql('SELECT * FROM database', conn)

conn.commit()
conn.close()
```

## SQLAlchemy

[documentation](https://docs.sqlalchemy.org/en/14/core/engines.html)

1. import the method `from sqlalchemy import create_engine`
2. create the engine by `engine = create_engine(*FILE_PATH_OF_THE DATABASE*)`
3. send a query to get the corresponding dataframe by `pd.read_sql(*SQL_query*, engine)`

```python3
from sqlalchemy import create_engine
import pandas as pd

engine = create_engine('database.db')
df = pd.read_sql('SELECT * FROM database', engine)
```
