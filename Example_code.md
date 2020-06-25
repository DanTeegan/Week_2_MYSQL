```sqlUSE northwind;

/*WHERE clause will filter the data*/
SELECT * FROM customers
WHERE City = 'paris';

SELECT * FROM Customers
WHERE City = 'London'

SELECT * FROM employees
WHERE titleofcourtesy = 'Dr.'

/*Use this to veiw the whole table*/
SELECT * FROM products
WHERE discontinued = '1'

/* This draws the number of emplyees from london with a count */
SELECT COUNT(*) AS "Number of employees taht are docters" FROM Employees
WHERE city = 'London'

SELECT COUNT(*) AS "Number of products discontinued" FROM products
WHERE discontinued = 1

SELECT companyName, City Country, Region
FROM customers WHERE region='BC'

/* This draws the number of emplyees from london with a count */
SELECT COUNT(*) AS "Number of employees taht are docters" FROM Employees
WHERE city = 'London'

/*Give the customers a nickname so it is easy to access*/
/* Called table aliasing */

SELECT c.CompanyName, c.City, c.Country, c.Region
FROM Customers c
WHERE c.Region='BC'

/*TOP is used when you want to select the top values of a table for example looking at highest employees paid*/
SELECT TOP 10 CompanyName, City FROM Customers
WHERE Country = 'France'

/*When you have more than one cirtera that needs to be filled we use AND*/
/*Using OR will mean either of the criteria needs to be fulfilled*/
SELECT ProductName, UnitPrice FROM Products
WHERE CategoryID = 1 AND Discontinued = '0'

/* An example of AND used with table aliasing */
SELECT p.ProductName, p.UnitPrice, p.CategoryID, p.Discontinued
FROM Products p
WHERE CategoryID = 1 AND Discontinued ='0'

/*An example of how we can use operators using the AND statment*/
SELECT p.ProductName, p.UnitPrice
FROM Products p
WHERE UnitsInStock > 0 AND UnitPrice > 29.99

/*Using DISTINCT means their are no dupicates. All unique values*/
SELECT DISTINCT c.Country
FROM Customers c
WHERE ContactTitle = 'Owner'

/* Used when you want to find out the countrys starting with the letter G */
SELECT c.Country
FROM Customers c
WHERE COUNTRY LIKE 'G%'

/* Used when you want to find out the last letter of the country. Also uses distinct function so their are no duplicates */
SELECT DISTINCT c.Country
FROM Customers c
WHERE COUNTRY LIKE '%A'

/* Used when you want to find out the last letter of the country. Also uses distinct function so their are no duplicates. Also it uses UPPER so data is present in CAPSLOCKS */
SELECT DISTINCT UPPER(c.Country)
FROM Customers c
WHERE COUNTRY LIKE '%A'

/*  This can be used when you want to draw data with a specific start anf end letter U%A */
SELECT DISTINCT c.Country
FROM Customers c
WHERE COUNTRY LIKE 'U%A'

/*When you want to draw data that has a variety of start letters*/
SELECT DISTINCT (c.Country)
FROM Customers c
WHERE COUNTRY LIKE '[UAM]%'

/*When you want to draw data that has a variety of end letters*/
SELECT DISTINCT (c.Country)
FROM Customers c
WHERE COUNTRY LIKE '%[UAM]'

/* When you want to draw the information with a accending order you use ORDER BY */
SELECT DISTINCT (c.Country)
FROM Customers c
WHERE COUNTRY LIKE '%[UAM]'
ORDER BY c.Country

/* When you want to draw the information with a desending order you use ORDER BY _____ DESC */
SELECT DISTINCT (c.Country)
FROM Customers c
WHERE COUNTRY LIKE '%[UAM]'
ORDER BY c.Country DESC

/* use ^ when you want data to not be starting in U A M*/
SELECT DISTINCT (c.Country)
FROM Customers c
WHERE COUNTRY LIKE '[^UAM]%'

/* Used when you want draw data where the third charecter is A */
SELECT DISTINCT (c.Country)
FROM Customers c
WHERE COUNTRY LIKE '__A%'

SELECT P.ProductName
FROM Products p
WHERE P.ProductName LIKE 'CH%'

/* Where you want the region to be 2 charecters with the second charecter being A */
SELECT *
FROM Customers 
WHERE region like '_A'

/* Using this statment instead of using IN Finding the region of WA OR SP AND also the country brazil*/
SELECT *
FROM customers
WHERE (Region = 'WA' OR Region = 'SP')
AND  country = 'Brazil'

/* This is an example of how to use the USE cluase shows the same information as the last one however it is simplified. using IN is better */
SELECT *
FROM customers
WHERE Region IN('WA','SP')
AND  country IN ('Brazil','USA')

/* Between is used to retereive the values between and also the boundry values */
SELECT *
FROM EmployeeTerritories
WHERE TerritoryID BETWEEN 06800 AND 09999

/* What are the names and product IDS of the products with a unit price below 5.00 */

SELECT p.ProductName, p.ProductID, P.UnitPrice
FROM products p
WHERE p.UnitPrice < 5.00

/* Which catogories have a category name with initials begining with B or S */

SELECT c.CategoryName
FROM Categories c
WHERE CategoryName LIKE '[BS]%'

/* HOW MANY ORDERS ARE THEIR FOR EMPLOYEE ID 5 AND 7 */
/* check the datatype of the emploees ID using sp_orders */
SELECT COUNT(*) AS "number of employee orders with emploersID 5 AND 7"
FROM Orders
WHERE EmployeeID IN (5,7);

/* This will show you individualy how many orders where placed by each employee GROUP BY */
SELECT COUNT(*) AS "number of employee orders with emploersID 5 AND 7"
FROM Orders
WHERE EmployeeID IN (5,7)
GROUP BY EmployeeID

/* This is an example of concatenation. This is where you join things together. In this example we are joining city and country  */
SELECT c.CompanyName AS "Company Name",
CONCAT(c.City, +', ', c.Country) AS "City"
FROM Customers c

/* Where you want to concatinate both first name and last name */
SELECT e.FirstName, e.LastName,
CONCAT(e.FirstName,' ', e.lastname) AS "Employee name"
FROM employees e

SELECT c.CompanyName AS "Company Name",
CONCAT(C.City, ', ', C.Country) AS "City"
FROM Customers c

/* Selecting the top 6 countrys that have region codes that are NOTNULL */
SELECT c.Region, C.Country
FROM Customers c
WHERE C.Region IS NOT NULL;

/*  */
SELECT o.UnitPrice,
o.Quantity,
o.Discount,
o.UnitPrice * o.Quantity AS "Gross total",
(o.UnitPrice*o.Quantity) - (o.UnitPrice*o.Discount*o.Quantity) AS "Net total"
FROM [Order Details]o

/* When you want to choose the 2 most expensive products in desending order */
SELECT TOP 2 o.UnitPrice,
o.Quantity,
o.Discount,
o.UnitPrice * o.Quantity AS "Gross total",
(o.UnitPrice*o.Quantity) - (o.UnitPrice*o.Discount*o.Quantity) AS "Net total"
FROM [Order Details]o
ORDER BY "Net total" DESC

SELECT PostalCode "Post Code",
LEFT(PostalCode, (CHARINDEX(' ',PostalCode))-1) AS "Post Code Region",
CHARINDEX (' ',PostalCode) AS "Space Found", Country
FROM Customers
WHERE Country ='UK'

SELECT DATEADD(10,5,orderdate) AS "DUE DATE"

SELECT p.productname
FROM Products p
WHERE p.productname LIKE '%'%



SELECT FROM

SELECT p.ProductName AS "Product Names",
CHARINDEX('''',p.ProductName) AS "Contains a Quote"
FROM Products p
WHERE CHARINDEX('''',P.ProductName) > 0

/* Calculating the date of purhase along with time taken to ship and then ship date */
SELECT DATEADD(d,5,c.OrderDate) AS "DUE DATE",
DATEDIFF(d, c.OrderDate, c.ShippedDate) AS "Ship Days"
FROM orders c

/* concatinating the first and last name and working out the age of each employee */
SELECT
CONCAT(e.FirstName, ' ' , e.LastName) AS "Employee Full Name",
DATEDIFF(YEAR, e.birthdate, GETDATE()) AS 'Age'
FROM Employees e

/* concatinating the first and last name and working out the age of each employee with rounding to 6 decimal places 
Also uses the day when when using DATEDIFF. You divide by 365.25 because we have selected to use days. It works out the differance between current date and birthdate*/
SELECT
CONCAT(e.FirstName, ' ' , e.LastName) AS "Employee Full Name",
ROUND(DATEDIFF(DAY, e.birthdate, GETDATE()) / 365.25,6) AS 'Age'
FROM Employees e

SELECT CASE
WHEN DATEDIFF(d,orderDate,ShippedDate) < 10 THEN 'On Time'
ELSE 'Overdue'
END AS "Status"
FROM orders 

/* This code will do the following:
first line will concatinate the first and last name
second line display the employees that are retired by using the >65 operator
third line will display the employees that have a retirment due by using >= 60
forth line will display ,oe than 5 to go
END AS is the name of this collum which data will be presented */
SELECT 
CONCAT(FirstName, ' ' , LastName) AS "Employee Full Name",
CASE
WHEN DATEDIFF(YEAR, birthdate, GETDATE()) > 65 THEN 'retired'
WHEN DATEDIFF(YEAR, birthdate, GETDATE()) >= 60 THEN 'Retirment Due'
ELSE 'More than 5 years to go'
END AS "Retirment Status"
FROM Employees;

/* This will calculate the sum, avg, min and max on the orders */
SELECT SupplierID, SUM(Unitsonorder) AS 'Total on order',
AVG(Unitsonorder) AS 'Average on order',
MIN(unitsonorder) AS 'Min on order',
MAX(Unitsonorder) AS 'Max on order'
FROM Products
GROUP BY SupplierID

/* Getting the average for the recorder level, grouping by category ID and ordering by desc  */
SELECT AVG(p.ReorderLevel) AS 'Average recorder level'
FROM Products p
GROUP BY P.CategoryID
ORDER BY "average recorder level" DESC

SELECT  AVG(p.CategoryID) AS 'Average recorder level'
FROM Products p
GROUP BY P.ReorderLevel

SELECT SupplierID, SUM(Unitsonorder) AS 'Total on order',
AVG(Unitsonorder) AS 'Average on order',
MIN(unitsonorder) AS 'Min on order',
MAX(Unitsonorder) AS 'Max on order'
FROM Products
GROUP BY SupplierID
HAVING AVG(Unitsonorder)>5

SELECT * FROM ORDERS





SELECT Customers.CustomerName, Orders.
FROM Customers
LEFT JOIN Orders
ON Customers.CustomerID=Orders.CustomerID
ORDER BY Customers.CustomerName;

SELECT COUNT(c.CustomerID) AS "Number of people living in the country", c.Country
FROM Customers c
GROUP BY c.Country
ORDER BY C.CustomerID DESC

SELECT c.
FROM customers c

SELECT e.EmployeeID, e.FirstName,o.OrderID,et.TerritoryID
FROM Orders o INNER JOIN Employees e 
ON o.EmployeeId=e.EmployeeId
INNER JOIN EmployeeTerritories et
ON et.EmployeeID=e.EmployeeID

sp_help products;
sp_help suppliers;

SELECT s.CompanyName AS "Supplier name", AVG(P.UnitsOnOrder) AS "Average"
FROM products p INNER JOIN suppliers s
ON p.SupplierID=s.SupplierID
GROUP BY S.CompanyName
ORDER BY "Average" DESC
```
