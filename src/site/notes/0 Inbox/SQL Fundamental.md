---
{"dg-publish":true,"permalink":"/0-inbox/sql-fundamental/","tags":["datacamp/sql"],"created":"2025-12-01T22:14:56.332+07:00","updated":"2025-12-12T22:00:22.122+07:00"}
---

A **database** is a system for managing data that allows us to store data reliably, retrieve information efficiently, and manipulate data systematically. Tables are composed of **rows and columns**. A row is sometimes called a "record" or "observation." 

Each column **represents a specific attribute or property**. A column is sometimes called a "field" or "attribute." Structured Query Language (**SQL**) is the most widely used programming language for working with data in databases.

The result of the query is a **temporary copy**. You have to intentionally save them to your computer or cloud if you want to keep the result for later use.

When working with database there are two system involved. 1.Database Server 2.Database Client (so called, **client-server architecture**)
And to connect, you would need the following data: 1. Server Address 2. Username and Password 3. Database Name

## Order of Execution
SQL **is not processed in its written order.**
This is good to know for debugging
`FROM, WHERE, GROUP BY, HAVING, SELECT, ORDER BY, LIMIT`
**Alias defined in `SELECT` cannot be used in `WHERE` clause due to order of execution but can be used in `ORDER BY` **

## Basic of SQL Query
`SELECT * FROM products;`
- Entire piece of code is called **SQL Query**
- ; is the statement terminator.
- `SELECT` and `FROM` are called **SQL Keywords**, it is convention to write this in uppercase. However, lowercase will still work.
- When selecting multiple field, try to add new line for each selection to make it easier for reading. (http://sqlstyle.guide/)
- IF the field name include the SPACE (non-standard field name), use double-quotes `"release year"` 

`ORDER BY rating DESC;`
will sort column rating (default = ascending order, add `DESC` for descending) 

`LIMIT 10;`
**Limiting is an essential practice because it prevents slow, expensive queries** and protects against mistakes that might return far more data than expected.

`SELECT DISTINCT category FROM products;` 
Use this to select unique categories.

`SELECT DISTINCT category AS unique_categories FROM products;`
Use `AS` keyword to assigns a new display name to the column that comes before it.

## Intermediate Statement
`SELECT COUNT(birthdate) AS count_birthdates FROM people;`
This will count number of the data in that column.
`SELECT COUNT(DISTINCT(birthdate)) AS count_distinct_birthdates FROM people;`
If you count a certain field, it will only count non-missing value. --> same result as adding `IS NOT NULL`
If you `COUNT(*)` it will include missing value (the `NULL`)
You have to use `AS` for each column if you want to alias each one.

### `WHERE` is a filtering clause.
`<>` = not equal to
When filtering string, use single quotes: `WHERE country = 'Japan'`
You can filter multiple criteria using `OR` `AND` `WHERE number BETWEEN __ AND __` (between is **inclusive**. It is like `>= AND <=)
You have to specify the field **for each condition** except the `WHERE` which will be specified in front of `BETWEEN` keyword.
Add `()` to ensure correct filter for multiple condition.

You can use these to filter for such a pattern in the text: `LIKE` , `NOT LIKE`, `IN`
Wildcards: `%` match zero, one or many characters (this is like * in SAP) , `_` match a single character (only 1 character)
This operation is **case-sensitive**
For example:
`SELECT name FROM people WHERE name LIKE 'Ade%` -> Return any name starting with Ade
`SELECT name FROM people WHERE name LIKE 'Ev_`  -> Return any name starting with Ev BUT only 1 character to be filled.
`SELECT name FROM people WHERE name LIKE '__t%` -> Return any name where the third character is t (and can be anything behind.)
SEE
`IN` Allow you to specify more value in the `WHERE` clause
For example: `WHERE release_year IN (1920, 1930, 1940)` OR `WHERE country IN ('Germany', 'France')`

Filter/ remove null value by using `IS NULL` or `IS NOT NULL`

### Aggregating Data
Aggregating perform the operation vertically
We should use the alias for this to make the returned field meaningful.
`AVG()` and `SUM()` can be used for **numerical field** only
`COUNT()` is also one of the aggregate function which does not count NULL
`MIN()` and `MAX()` (also `COUNT()`) can be used for **non_numerical field**
For the min and max, if it is character, lowest is A and the highest is Z character
It is always best practice to aggregate the field name to make it easier for reading the result and code.
`ROUND()` can be added to round the result / number. You can also specify decimal wanted such as `ROUND(AVG(budget), 2)` You can round to a negative number (`ROUND(AVG(budget), -3)`   <-- nearest thousand) 

### Aliasing and arithmetic
Arithmetic perform the operation horizontally
We always need to use the alias for this as it always return default field name (`?column?`)
`4/3` return `1` because **SQL thinks** we want the answer to be an integer.
`4.0 / 3.0` return `1.333 repeating..`

### Sorting Result
`ORDER BY budget;` will sort `ASC` by default. Use `DESC` for descending.
The field to be used in `ORDER BY` does not need to be selected via `SELECT`
You can sort by multiple field
`ORDER BY field_one ASC, field_two DESC`

### Grouping Result
`GROUP BY certification;` mostly used with aggregation.
You can also `GROUP BY` multiple fields.
You can also use `GROUP BY` with `ORDER BY`
```sql
SELECT
	certification,
	COUNT(title) AS title_count
FROM films
GROUP BY certification
ORDER BY title_count DESC
LIMIT 3;
```
If we want to **FILTER** the result based on the result of an aggregate function, you have to use `HAVING`
```SQL
SELECT
	certification,
	COUNT(title) AS title_count
FROM films
WHERE certifications
	IN ('G', 'PG')
GROUP BY certification
HAVING COUNT(title) > 500
ORDER BY title_count DESC
LIMIT 3;
```