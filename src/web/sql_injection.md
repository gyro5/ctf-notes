# SQL Injection

## Quickly check for SQL injection vulnerability

Classic test: `' OR 1=1 --`.

## About `UNION SELECT`

`UNION` is a SQL keyword to combine the results of 2 separate `SELECT` queries. For example:

```sql
SELECT 1 UNION SELECT 2;
```

```text
1|
-+
1|
2|
```

Thus, `UNION` is a way to piggy back an existing query and get what we want from the database. Separating 2 queries with `;` may not work as most database drivers will just execute one statement.

`UNION` also requires both queries to have matching column counts and compatible column data types (but does not require the same column names). 

To find the number of columns in the original query, try `ORDER BY` with different column numbers until getting an error:

```text
' ORDER BY 1 --
' ORDER BY 2 --
' ORDER BY 3 --
```

The number points to the column shown in the query result, for example: `1` means the first column. An error means that column number is out of bound, aka the number of columns is one less than that.
