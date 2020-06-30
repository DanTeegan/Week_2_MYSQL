
## Objectives
1.	Demonstrate the ability to connect to a database and query it.
2.	Write simple SQL statements to alter and add data.
3.	Write simple queries to extract and compare data.
4.	Demonstrate an ability to research and learn technical skills independently.

### Operators

1. There `<>` Or `!=` Not equal to.
2. `<` Less than 
3. `>`	More than
4. `<=` Less than or equal to
5. `>=` Greater than or equal too

### Wildcards

Wildcards can be used as a substitute for any other characters in a string when using the LIKE operator.

- `%` = A substitute for zero or more characters

- `_` = A substiture for a single character

- `[charlist] `= Sets and ranges of characters to match I.E. `LIKE[ABC]%` . This will bring back anything starting with any of those letters.
- `[^charlist]` Sets and ranges of characters that don’t match I.E. `LIKE[^ABC]%` . This will bring back anything that does not start with those letters.
 
### Filtering results based on NULLs
In order to filter based on NULLs simply use IS NULL or IS NOT NULL.

### String functions

The following string functions can be used to manipulate text in various ways in the SELECT clause

1.	SUBSTRING – `SUBSTRING(expression, start, length)` SUBSTRING(name,1,1) for the initial
2.	CHARINDEX - `CHARINDEX(‘a’, ‘text’` TO search for a string, e.g. find “a” in a column called text.
3.	LEFT or RIGHT – `LEFT(name,5)` For the first (or last) 5 characters
4.	LTRIM or RTRIM – Used to remove spaces at the beginning or end of a string.
5.	LEN – `LEN(Name)` for the length of the name.
6.	REPLACE – `REPLACE(name,’ ‘,’_’)` To replace spaces with underscores.
7.	UPPER or LOWER – `UPPER(name)` to convert to all upper or lower case
