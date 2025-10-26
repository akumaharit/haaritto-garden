---
{"dg-publish":true,"permalink":"/0-inbox/cs-50-sql/","tags":["cs50web","sql"],"created":"2025-10-26T11:49:49.812+07:00","updated":"2025-10-26T20:47:12.922+07:00"}
---

you can use sql to work with python classes or object (known as **model**)
migration is a technique to make the django update underlying model
Django will create these SQL queries for us.

## Data
each column = 1 field
each row = 1 observation
SQL used to interact with relational database system
- MySQL
- PostgreSQL
- SQLite -> light implemenation of sql standard, store all data inside a single file
Each has pro and con and difference features (including difference supported data type)

## SQLite Types
- Text
- Numeric -> number like data, boolean, date, or any other that does not store in integer and real
- Integer 
- Real -> decimal point etc.
- Blob -> binary data

## MySQL Types
- Char(size) -> will always store with length 'size' (space will be added)
- Varchar(size) -> no space will be added
- Smallint
- int
- bigint
- float
- double
## Creating SQL
```sql
CREATE TABLE flights (
	id INTEGER PRIMARY KEY AUTOINCREMENT,
	origin TEXT NOT NULL
	destination TEXT NOT NULL,
	duration INTEGER NOT NULL
);
```
NOT NULL is a **constraint** telling that this field CANNOT BE EMPTY
AUTOINCREMENT to automatically update the id every time I add a new row.

### other constraint example
CHECK -> data validation e.g. to make it check if the data is within range of 1-5
DEFAULT -> default data
NOT NULL
PRIMARY KEY
UNIQUE -> to guarantee that the column will be UNIQUE (enforcing it)

## Insert Data in SQL
```sql
INSERT INTO flights
	(origin, destination, duration)
	VALUES ("New York", "London", 415);
```

| Part                                     | Meaning                                                                                            |
| ---------------------------------------- | -------------------------------------------------------------------------------------------------- |
| **`INSERT INTO flights`**                | Tells the database that you want to **add a new record (row)** into the table named **`flights`**. |
| **`(origin, destination, duration)`**    | Specifies **which columns** you are providing values for in this table.                            |
| **`VALUES ("New York", "London", 415)`** | Gives the **actual values** to be inserted into those columns, **in the same order**.              |

## Retrieve data in SQL
```sql
SELECT * FROM flights;
```
`*` mean select all of the column
```sql
SELECT * FROM flights WHERE id = 3;*
SELECT * FROM flights WHERE origin = "New York";
SELECT * FROM flights WHERE duration > 500 AND destination = "Paris";
SELECT * FROM flights WHERE origin IN ("New York", "Limia");

```
this will return only row where ID = 3
and another will return where origin = "New York"
the boolean expression and logical operator also work
```sql
SELECT * FROM flights WHERE origin LIKE "%a%";
```
this is like `*a*` in SAP -> anything that has a in it.
### Functions
- Average
- Count
- Max
- Min
- Sum
## Creating SQLite database
Just create a file with `.sql` extension.
Then `sqlite3 __.sql` it will then access the file.
`.tables` to check for all the table in the database.
`.mode columns` to change to columns mode
`.headers yes` to add headers

## Update Database
```sql
UPDATE flights
	SET duration = 430
	WHERE origin = "New York"
	AND destination = "London";
```

## DELETE Database
```sql
DELETE FROM flights WHERE destination = "Tokyo";
```
This will delete all row where destination = "Tokyo";

## Other Clauses
LIMIT
ORDER BY
GROUP BY
HAVING -> constraint to place by GROUP BY (e.g. I want to group by _______ having sum of ______)


## Joining Table