---
{"dg-publish":true,"permalink":"/0-inbox/sql-fundamental/","tags":["datacamp/sql"],"created":"2025-12-01T22:14:56.332+07:00","updated":"2025-12-06T11:18:51.982+07:00"}
---

A **database** is a system for managing data that allows us to store data reliably, retrieve information efficiently, and manipulate data systematically. Tables are composed of **rows and columns**. A row is sometimes called a "record" or "observation." 

Each column **represents a specific attribute or property**. A column is sometimes called a "field" or "attribute." Structured Query Language (**SQL**) is the most widely used programming language for working with data in databases.

The result of the query is a **temporary copy**. You have to intentionally save them to your computer or cloud if you want to keep the result for later use.

When working with database there are two system involved. 1.Database Server 2.Database Client (so called, **client-server architecture**)
And to connect, you would need the following data: 1. Server Address 2. Username and Password 3. Database Name

### Order of Execution
SQL **is not processed in its written order.**
This is good to know for debugging

### Basic of SQL Query
`SELECT * FROM products;`
- Entire piece of code is called **SQL Query**
- ; is the statement terminator.
- `SELECT` and `FROM` are called **SQL Keywords**, it is convention to write this in uppercase. However, lowercase will still work.

`ORDER BY rating DESC;`
will sort column rating (default = ascending order, add `DESC` for descending) 

`LIMIT 10;`
**Limiting is an essential practice because it prevents slow, expensive queries** and protects against mistakes that might return far more data than expected.

`SELECT DISTINCT category FROM products;` 
Use this to select unique categories.

`SELECT DISTINCT category AS unique_categories FROM products;`
Use `AS` keyword to assigns a new display name to the column that comes before it.

### Intermediate Statement
`SELECT COUNT(birthdate) AS count_birthdates FROM people;`
This will count number of the data in that column.
`SELECT COUNT(DISTINCT(birthdate)) AS count_distinct_birthdates FROM people;`
