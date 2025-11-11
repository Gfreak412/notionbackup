- `SELECT * FROM ``*file_name*`
- `LIMIT = 10` (always at the end of query)
- `WHERE` can only be used once, and it cannot filter aggregate columns (like - count, sum, min/max, avg)
- `SELECT * FROM ``*file_name WHERE*`` month ≠ ‘January’ ( ’ ’ single quotes to reference column values)``* *`
### Query clause order
As mentioned in prior lessons, the order in which you write the clauses is important. Here's the order for everything you've learned so far:
1. `SELECT`
1. `FROM`
1. `WHERE`
1. `GROUP BY`
1. `HAVING`
1. `ORDER BY`
### Comparison Operators
| Equal to | `=` | 
| ---- | ---- | 
| Not equal to | `<>` or `!=` | 
| Greater than | `>` | 
| Less than | `<` | 
| Greater than or equal to | `>=` | 
| Less than or equal to | `<=` | 
### Logical Operators (Generally used with `WHERE` )
- `**[LIKE](https://mode.com/sql-tutorial/sql-like)**` allows you to match similar values, instead of exact values.
- `SELECT * FROM tutorial.billboard_top_100_year_end WHERE "group_name" LIKE 'Snoop%'`
- `SELECT * FROM tutorial.billboard_top_100_year_end WHERE "group_name" ILIKE snoop%'`
or
- `SELECT * FROM tutorial.billboard_top_100_year_end WHERE artist ILIKE 'dr_ke'`
- `**[IN](https://mode.com/sql-tutorial/sql-in-operator)**` allows you to specify a list of values you'd like to include.\
- ` SELECT * FROM tutorial.billboard_top_100_year_end `
` WHERE artist IN ('Taylor Swift', 'Usher', 'Ludacris')`
- `**[BETWEEN](https://mode.com/sql-tutorial/sql-between)**` allows you to select only rows within a certain range (ex. `BETWEEN 5 AND 10`).
- `**[IS NULL](https://mode.com/sql-tutorial/sql-is-null)**` allows you to select rows that contain no data in a given column.
- `**[AND](https://mode.com/sql-tutorial/sql-and-operator)**` allows you to select only rows that satisfy two conditions.
- `**[OR](https://mode.com/sql-tutorial/sql-or-operator)**` allows you to select rows that satisfy either of two conditions.
- `**[NOT](https://mode.com/sql-tutorial/sql-not-operator)**` allows you to select rows that do not match a certain condition.
<br/>
### ORDER BY
`SELECT * FROM tutorial.billboard_top_100_year_end
WHERE year_rank <= 3
ORDER BY year DESC, year_rank` 
### CASE
- Syntax - `CASE WHEN ‘……’ THEN ‘……’ ELSE '……’ END AS ``*column_nam*``e` 
`GROUP BY` 
### DISTINCT
- `SELECT DISTINCT year, month
FROM tutorial.aapl_historical_stock_price`
