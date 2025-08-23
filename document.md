# Introduction to SQL

SQL (Structured Query Language) is used to communicate with relational databases. It allows you to create, read, update, and delete (CRUD) data, along with performing queries for analysis. SQL is used to manage and manipulate the data in the Database. SQL is used on the data that is stored in rows and columns format, simply Tables. SQL is not case-sensitive.

# Basics


To store data in the Database we create tables, data stored in row and column wise. After creating tables we need to insert data in to those tables. In this way we can create, update, delete data from the table accordingly. There are different types of keywords are there to manipulate database. Lets create table for employee in a company.

## Create Table Example:
```
    CREATE TABLE Employees (
		Employee_ID INT PRIMARY KEY,  ----->	(variable_name, datatype, unique identifier for table)
		First_name VARCHAR(50),	      ----->    (variable_name, datatype(size))
		Last_name VARCHAR(50),
		Department_ID INT,
		Salary DECIMAL(10,2)
    );
```

Table is created. But it is empty, till we put or insert data into it. So we need to insert data into it. We have keywords to insert data into tables. Those are 'insert into' and 'values'. We need specify the table name to insert data into it and need follow the order how the variables are declared in the table. In the same order we need to insert values into it. We can do multiple insertions at a time by using a ',' separator.

## Insert Data Example:
```
    INSERT INTO Employees (Employee_ID, First_name, Last_name, Department_ID, Salary) VALUES
    (1, 'Arjun', 'Reddy', 101, 60000),
    (2, 'Bheeshma', 'Naidu', 102, 55000),
    (3, 'Chiranjeevi', 'Sastry', 101, 70000),
    (4, 'Deepak', 'Mishra', 103, 50000);
```

There are some basic keywords are there to manipulate or retrieve data from the database. Those are helpful for update, manage, make analysis out of it. Those queries are helpful to directly interact with the database.

## Some basic Queries on Tables

```
    -- Select all employees
    SELECT * FROM Employees;

    -- Select specific columns
    SELECT First_name, Last_name, Salary FROM Employees;

    -- Filtering results
    SELECT * FROM Employees WHERE Salary > 55000;

    -- Sorting results
    SELECT * FROM Employees ORDER BY Salary DESC;

    -- Update a record
    UPDATE Employees SET Salary = 65000 WHERE Employee_ID = 2;

    -- Delete a record
    DELETE FROM Employees WHERE Employee_ID = 4;
```


# Joins

Joins are used to combine rows from two or more tables. Joins are used to extract the data from two or more tables at a time in the way we want. These are used to analyze the data between tables.

## Inner Join

Returns records with matching values in both tables.

```
    SELECT e.First_name, e.Last_name, d.Department_name
    FROM Employees e
    INNER JOIN Departments d
    ON e.Department_ID = d.Department_ID;
```

### Explanation:
Here select is used to extract data from different tables and e, d are used to represent the tables for our convenience and used inner join. Here department id is primary key , because it is unique for both the tables.


## Left Join
Returns all rows from the left table, along with matching rows from the right table. If there is no match, NULL values are returned.

```
    SELECT e.First_name, e.Last_name, d.Department_name
    FROM Employees e
    LEFT JOIN Departments d
    ON e.Department_ID = d.Department_ID;
```

### Explanation: 
SELECT keyword selects First_name and Last_name form Employee table and selects Department_name from Department table on a condition if Department_ID is equal.


## Right Join
Returns all the rows of the table, along with matching rows from the left table. It is very similar to LEFT JOIN. If there is no matching row on the left table, the result-set will contain null values.

```
    SELECT e.First_name, e.Last_name, d.Department_name
    FROM Employees e
    RIGHT JOIN Departments d
    ON e.Department_ID = d.Department_ID;
```

### Explanation: 
SELECT keyword selects First_name and last_name from the Employee table and uses RIGHT JOIN on Department table on a condition if Department_ID is Equals on both the tables.


## Full Join
Full Join will create the result set by combining the results of both Left Join and Right Join. It contains all the rows from both the tables, if there are unmatched rows then the result set contains null values.

```
    SELECT e.First_name, e.Last_name, d.Department_name
    FROM Employees e
    FULL OUTER JOIN Departments d
    ON e.Department_ID = d.Department_ID;
```

### Explanation: 
Full Outer Join is a combination of Left and Right Joins. It retrieves records/rows from both the tables , if there are rows form one tables which are not in other table, the result will contain null values.


# Aggregations

Aggregate functions in SQL perform some calculations on more than one value to return a single value. SQL has many aggregate functions, including average, count, sum, min, and max. All aggregate functions ignore NULL values while calculating, except the Count function.

There are five types of SQL aggregate functions:

- Count()
- Sum()
- Avg()
- Min()
- Max()

### Count()

The COUNT() function returns the number of rows in a database table.

	SELECT count(*) AS TotalEmployees FROM Employees;
	

### Sum()

The SUM() function returns the sum of all values in a database table.

	SELECT SUM(salary) AS Total FROM Employees;


### Avg()

The AVG() function returns the Average of all the values.

	SELECT AVG(Salary) AS AverageSalary FROM Employees;
	

### Min() / Max()

The MIN() / MAX() functions returns the Min / Max value from the table.
	
	SELECT MAX(Salary) AS HighestSalary FROM Employees;
	SELECT MIN(Salary) AS LowestSalary FROM Employees;
	
	


# References:

- [Geeks for Geeks](https://www.geeksforgeeks.org/sql/sql-join-set-1-inner-left-right-and-full-joins/)

- [Simplelearn](https://www.simplilearn.com/tutorials/sql-tutorial/sql-aggregate-functions)
