### Date functions

The following date functions can be used to manipulate data in various ways in the `SELECT` clause
`DATE` Functions 
- GETDATE select `GETDATE()` to return the current date and time 

- SYSDATETIME `SELECT SYSDATETIME()` to retutn the date and time of the computer being used

- DATEADD `DATEADD(d,5,OrderDate)` AS "DueDate" to add 5 days

- DATEDIFF `DATEDIFF(d,OrderDate,ShippedDate)` AS "Ship Time" to calculate difference between dates 

- YEAR `SELECT YEAR(OrderDATE)` AS "Order Year" to extract the year from a date. 

- MONTH: `SELECT MONTH(OrderDate)` AS "Order Month" to extract the year from a date 

- DAY: `SELECT DAY (OrderDate)` AS "Order Day" to extract the day from a date


### CASE statements 

`CASE` statements can be useful when you need varying results output based on differing data.
Pay close attention to `WHEN THEN ELSE and END`.

Use single quotes for data and double quotes for column aliases.
Below is an example of using the CASE statement:
```
SELECT 
CONCAT(FirstName, ' ' , LastName) AS "Employee Full Name",
CASE
WHEN DATEDIFF(YEAR, birthdate, GETDATE()) > 65 THEN 'retired'
WHEN DATEDIFF(YEAR, birthdate, GETDATE()) >= 60 THEN 'Retirment Due'
ELSE 'More than 5 years to go'
END AS "Retirment Status"
FROM Employees;

```

### Aggregate functions

The following aggregate functions can be used to calculate totals usually in conjuction with the GROUP BY clause.

1. SUM – `SUM(OrderTotal)` for the grand total of a column for all rows selected.

2. AVG – `AVG(UnitPrice)` for the average of a column for all rows selected.

3. MIN – `MIN(UnitPrice)` for the smallest value in a column for all rows selected.

4. MAX – `MAX(UnitPrice)` for the largest value in a column for all rows selected.

5. COUNT – `COUNT(*)` for the numbers of NOT NULL rows selected. If * is used then all rows are counted

### HAVING CLAUSE

`HAVING` is used instead of `WHERE` when filtering on subtotals/grouped data.

Column Aliases cannot be used in the `HAVING` clause

Aggregate functions are not available for use in the `WHERE` clause due to the SQL processing.

### JOINs

JOIN is an SQL keyword used to combine matched rows from two or more tables.
It allows you to create a list of combined rows of matching data from different tables.

1. `INNER JOIN`
2. `LEFT JOIN`
3. `RIGHT JOIN`
4. `OUTER JOIN`
5. `SELF JOIN`

SEE PRESENTATIONS ABOUT JOINS FOR MORE INFORMATION
