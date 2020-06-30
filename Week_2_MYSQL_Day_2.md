## Week 2 MY SQL Day 2

### Structured query language
1.	Data manipulation language
2.	Data definition language
3.	Data control language – privileged rights of the user. Given by the database administrator.
4.	Transaction control language - 

### DML – main focus related to data
1.	`SELECT`
2.	`INSERT`
3.	`UPDATE`
4.	`DELETE` – Deleting data within a table

### DDL – main focus related to structure
1.	`CREATE`
2.	`ALTER`
3.	`DROP` – Dropping the whole table. Delete table and data.
4.	`TRUNCATE` – Gets you all the data out of the table. Does not drop the table. Keeps the table empty.

### DCL
1.	`GRANT` – Grant a user privileges to the database
2.	`REVOKE` – Revoke a user’s privileges of the database

### TCL
1.	`COMMIT`
2.	`ROLLBACK` – same as undo
3.	`SAVEPOINT`



### Datatypes
1. `VARCHAR` – adaptable to different lengths of characters. Records MAX size. Memory efficient. Commonly used for things such as name.

2. `CHARACTER` or `CHAR` – 50% faster than VARCHAR. Example of using CHAR might be on a car licence plate or phone numbers. Anything where the number of characters is known. Data must be fixed amount of space.

3. `INT` – holds a whole number/integer.

4. `DATE` or `TIME` or `DATETIME`- stores date, time or both date and time.

5. `DECIMAL` OR `NUMERIC` – Fixed precision and scale(digits to the right of the decimal point)

6. `BINARY` – used to store binary data such as an image or file

7. `FLOAT` – Scientific use (very large numbers)

8. `BIT` – equivalent to binary (0, 1 or null)

### NOTE IMPORTANT
- Always check that the date is presented like `2002/08/17` when inserting data into a row.
- When inserting `VARCHAR`, `CHAR`, `DATE` and `DATETIME` use single quotes.
- All other data types don’t need single quotes.
- Use `;` after each statement
- `IDENTITY(1,1)`  1+1=2, 3, 4, 5



### Variations on INSERT

Changing the order of the columns

 - if you have already created a table, the order in which you add the data doesn’t have to be the same as the original column order as long as the values match the order you are now inserting
Omitting column name
- You don’t have to put the column names in, but the values have to be in the same order as the original columns
Leaving some columns out
You can leave some information out; it doesn’t have to be inserted with the rest. For this you will have to specify the column names the values are going into.

### NULL
1.	`NULL` is not nothing, but it does not equate to zero.
2.	It isn’t even an empty string.
3.	A value can be `NULL`, but `NULL` never equals NULL because `NULL` is an undefined value.

### Database Considerations
1.	Data security
2.	Rata recovery
3.	Data integrity
4.	Normal form

### Normalisation
Normalisation is what we do to attain a better design and a better performance. We reduce all the redundant values from the database. An example of these redundant values are repeated values.

### 1st Normal form

A database is in First Normal Form when the following considerations are satisfied.
Make everything atomic
1.	Data must be presented as small as it can be

2.	There should be no repeating groups
For example A table that records data on a book and its author(s) with the following columns: `[Book ID], [Author1],[Author2], [Author3]` is not in 1NF because `[Author1],[Author2] and [Author3]` are all repeating the same attribute.
How can we make this 1NF?

![IMAGE]( https://imgur.com/tA8hSgH)

![IMAGE]( https://ibb.co/NxhPmq2)

### 2nd Normal Form
1.	A database is in Second Normal Form when he following conditions are satisfied:
2.	It is in 1NF
3.	All non-key attributes are fully functional dependent on the primary key


Here a composite key is used, “Product ID and “Store” combine to make the primary key
In this case “Location” only depends on “store” which is only part of the primary key.
![IMAGE]( https://ibb.co/zN1ZWTV)
![IMAGE]( https://ibb.co/bKk0JP2)


### 3rd Normal Form
A database is in Third Normal Form when the following conditions are satisfied:
1.	It is in 2NF
2.	There is no transitive functional dependency. For example

A transitive functional dependency is when a non-key column is functionally dependent on another non-key column, which is functionally dependent on the primary key.


In this example Book ID determines Genre ID, which in turn determines Genre Type – that means they are functionally dependent on each other.

![IMAGE]( https://ibb.co/bKk0JP2)

![IMAGE]( https://ibb.co/NFKHtMn)

`ON DELETECASCADE` = A foreign key with cascade delete means that if a record in the parent table is deleted, then the corresponding records in the child table will automatically be deleted. This is called a cascade delete in SQL Server.

![IMAGE]( https://ibb.co/NFKHtMn)


