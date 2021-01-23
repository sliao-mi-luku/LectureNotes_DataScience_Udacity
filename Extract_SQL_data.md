# Extract SQL Data

## sqlite3

The library **sqlite3** can be used to extract SQL data:


**Example 1**

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


**Example 2**

```python3
conn = sqlite3.connect('database.db')

cur = conn.cursor()

# drop the test table if it already exists
cur.execute("DROP TABLE IF EXISTS test")

# create the test table including project_id as a primary key
cur.execute("CREATE TABLE test (project_id TEXT PRIMARY KEY, contryname TEXT, countrycode TEXT, totalamt REAL, year INTEGER);"

# insert a value into the test table
cur.execute("INSERT INTO test (project_id, countryname, countrycode, totalamt, year) VALUES ('a', 'Brazil', 'BRA', '100,000', 1970);")

# commit changes
conn.commit()

cur.execute("SELECT * FROM test")
cur.fetchall()

conn.close() 
```

**Example 3**

Inserting values into the table

```python3

## Create the table
cur.execute("CREATE TABLE data_table (id TEXT, name TEXT, score INTEGER, PRIMARY KEY (id, name));") # this is how to set multiple columns as primary keys

## Suppuse we have some variables storing the value we need (id = id_value, name = name_value, score = score_value)

## Insert the values into the table
sql_insert_command = 'INSERT INTO data_table (id, name, score) VALUES ("{}", "{}", {});'.format(id_value, name_value, score_value)
cur.execute(sql_insert_command)

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
