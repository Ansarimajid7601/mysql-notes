# Definition of Database

A **database** is an organized collection of structured information, or data, typically stored electronically in a computer system. A database is usually controlled by a database management system (DBMS). Together, the data and the DBMS, along with the applications that are associated with them, are referred to as a database system, often shortened to just database.

## Database Languages

### 1. SQL (Structured Query Language)

SQL is the standard language for relational database management systems. SQL statements are used to perform tasks such as update data on a database, or retrieve data from a database.

### 2. PL/SQL (Procedural Language/SQL)

PL/SQL is a procedural language extension for SQL, used in Oracle databases. It combines the data manipulation power of SQL with the processing power of procedural languages.

### 3. T-SQL (Transact-SQL)

T-SQL is an extension of SQL used in Microsoft SQL Server and Sybase ASE. It includes procedural programming, local variables, and various support functions for string processing, date processing, mathematics, etc.

### 4. NoSQL (Not Only SQL)

NoSQL databases provide a mechanism for storage and retrieval of data that is modeled in means other than the tabular relations used in relational databases. These databases are used in big data and real-time web applications.

### 5. MongoDB Query Language (MQL)

MQL is the query language used in MongoDB, a NoSQL database. It is designed for working with JSON-like documents and provides a rich set of operators to perform various operations on the data.

## Database Commands

### 1. DDL (Data Definition Language)

DDL statements are used to define and manage database objects such as tables, indexes, and schemas. Common DDL commands include `CREATE`, `ALTER`, `DROP`, and `TRUNCATE`.

### 2. DML (Data Manipulation Language)

DML statements are used for managing data within schema objects. These commands include `SELECT`, `INSERT`, `UPDATE`, and `DELETE`.

### 3. DCL (Data Control Language)

DCL statements are used to control access to data in the database. The primary DCL commands are `GRANT` and `REVOKE`, which are used to give or remove user access privileges to the database objects.

### 4. TCL (Transaction Control Language)

TCL statements are used to manage transactions in the database. These commands include `COMMIT`, `ROLLBACK`, and `SAVEPOINT`.

### 5. REST (Representational State Transfer)

REST is an architectural style for designing networked applications. It relies on a stateless, client-server, cacheable communications protocol -- the HTTP. RESTful applications use HTTP requests to perform CRUD operations (Create, Read, Update, Delete) on resources, which are typically represented by JSON or XML.

## Creating a Database Table

To create a database table, you use the `CREATE TABLE` statement. Here is an example of creating a table named `employees`:

```sql
CREATE TABLE employees (
    id INT PRIMARY KEY,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    email VARCHAR(100),
    hire_date DATE
);
```

## Inserting Data into a Table

To insert data into a table, you use the `INSERT INTO` statement. Here is an example of inserting a record into the `employees` table:

```sql
INSERT INTO employees (id, first_name, last_name, email, hire_date)
VALUES (1, 'John', 'Doe', 'john.doe@example.com', '2023-01-15');
```

## Updating Data in a Table

To update existing data in a table, you use the `UPDATE` statement. Here is an example of updating the email of an employee in the `employees` table:

```sql
UPDATE employees
SET email = 'john.newemail@example.com'
WHERE id = 1;
```

## Deleting Data from a Table

To delete data from a table, you use the `DELETE` statement. Here is an example of deleting a record from the `employees` table:

```sql
DELETE FROM employees
WHERE id = 1;
```

## Using the LIKE Operator

The `LIKE` operator is used in a `WHERE` clause to search for a specified pattern in a column. Here is an example of using the `LIKE` operator to find employees whose first name starts with 'J':

```sql
SELECT * FROM employees
WHERE first_name LIKE 'J%';
```

%j is zero--find the value that start with J
%j is zero--find the value that ends with J
%j% is zero--find the value with J in any position

In this example, the `%` wildcard matches zero or more characters. You can also use the `_` wildcard to match a single character. For example, to find employees whose first name is exactly four characters long and starts with 'J', you can use:

- is one single chracter

```sql
SELECT * FROM employees
WHERE first_name LIKE 'J___';
```

-r% find the value in second position

## Using the HAVING Clause

The `HAVING` clause is used to filter records that work on summarized `GROUP BY` results. It is similar to the `WHERE` clause but is used with aggregate functions. Here is an example of using the `HAVING` clause to find departments with more than 10 employees:

```sql
SELECT department_id, COUNT(*)
FROM employees
GROUP BY department_id
HAVING COUNT(*) > 10;
```

## Using Aggregate Functions

Aggregate functions perform a calculation on a set of values and return a single value. Common aggregate functions include `COUNT`, `SUM`, `AVG`, `MIN`, and `MAX`. Here are some examples:

### COUNT

The `COUNT` function returns the number of rows that match a specified condition. For example, to count the number of employees in the `employees` table:

```sql
SELECT COUNT(*)
FROM employees;
```

### SUM

The `SUM` function returns the total sum of a numeric column. For example, to find the total salary of all employees:

```sql
SELECT SUM(salary)
FROM employees;
```

### AVG

The `AVG` function returns the average value of a numeric column. For example, to find the average salary of employees:

```sql
SELECT AVG(salary)
FROM employees;
```

### MIN

The `MIN` function returns the smallest value in a column. For example, to find the lowest salary among employees:

```sql
SELECT MIN(salary)
FROM employees;
```

### MAX

The `MAX` function returns the largest value in a column. For example, to find the highest salary among employees:

```sql
SELECT MAX(salary)
FROM employees;
```

## Using Keys in a Database

### Primary Key

A primary key is a field in a table which uniquely identifies each row/record in that table. Primary keys must contain unique values, and cannot contain NULL values. A table can have only one primary key, which may consist of single or multiple columns. Here is an example of defining a primary key:

```sql
CREATE TABLE employees (
    id INT PRIMARY KEY,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    email VARCHAR(100),
    hire_date DATE
);
```

### Foreign Key

A foreign key is a field (or collection of fields) in one table that refers to the primary key in another table. The foreign key constraint is used to prevent actions that would destroy links between tables. Here is an example of defining a foreign key:

```sql
CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    order_date DATE,
    employee_id INT,
    FOREIGN KEY (employee_id) REFERENCES employees(id)
);
```

### Unique Key

A unique key is a constraint that ensures all values in a column are unique. Unlike primary keys, a table can have multiple unique keys. Here is an example of defining a unique key:

```sql
CREATE TABLE employees (
    id INT PRIMARY KEY,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    email VARCHAR(100) UNIQUE,
    hire_date DATE
);
```

### Composite Key

A composite key is a primary key composed of multiple columns used to identify a record uniquely. Here is an example of defining a composite key:

```sql
CREATE TABLE employee_projects (
    employee_id INT,
    project_id INT,
    PRIMARY KEY (employee_id, project_id)
);
```

### Super Key

A super key is a set of one or more columns (attributes) that can uniquely identify a row in a table. A super key may contain additional attributes that are not necessary for unique identification. Here is an example of defining a super key:

```sql
CREATE TABLE employees (
    id INT,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    email VARCHAR(100),
    hire_date DATE,
    UNIQUE (id, email)
);
```

## Join Operations

Join operations are used to combine rows from two or more tables based on a related column between them. Here are some common types of joins:

### INNER JOIN

The `INNER JOIN` keyword selects records that have matching values in both tables. Here is an example of using an `INNER JOIN` to combine the `employees` and `orders` tables:

```sql
SELECT employees.id, employees.first_name, orders.order_id
FROM employees
INNER JOIN orders ON employees.id = orders.employee_id;
```

### LEFT JOIN (or LEFT OUTER JOIN)

The `LEFT JOIN` keyword returns all records from the left table (table1), and the matched records from the right table (table2). The result is `NULL` from the right side if there is no match. Here is an example:

```sql
SELECT employees.id, employees.first_name, orders.order_id
FROM employees
LEFT JOIN orders ON employees.id = orders.employee_id;
```

### RIGHT JOIN (or RIGHT OUTER JOIN)

The `RIGHT JOIN` keyword returns all records from the right table (table2), and the matched records from the left table (table1). The result is `NULL` from the left side when there is no match. Here is an example:

```sql
SELECT employees.id, employees.first_name, orders.order_id
FROM employees
RIGHT JOIN orders ON employees.id = orders.employee_id;
```

### FULL JOIN (or FULL OUTER JOIN)

The `FULL JOIN` keyword returns all records when there is a match in either left (table1) or right (table2) table records. Here is an example:

```sql
SELECT employees.id, employees.first_name, orders.order_id
FROM employees
FULL JOIN orders ON employees.id = orders.employee_id;
```

### CROSS JOIN

The `CROSS JOIN` keyword returns the Cartesian product of the two tables, i.e., it returns all possible combinations of rows from the tables. Here is an example:

```sql
SELECT employees.id, employees.first_name, orders.order_id
FROM employees
CROSS JOIN orders;
```

### SELF JOIN

A `SELF JOIN` is a regular join but the table is joined with itself. Here is an example:

```sql
SELECT e1.id, e1.first_name, e2.first_name AS manager_name
FROM employees e1
INNER JOIN employees e2 ON e1.manager_id = e2.id;
```

### CROSS OUTER JOIN

The `CROSS OUTER JOIN` is not a standard SQL join type. However, you can achieve similar results by combining a `CROSS JOIN` with a `LEFT JOIN` or `RIGHT JOIN` to include all records from one table and the Cartesian product with the other table. Here is an example using `LEFT JOIN`:

```sql
SELECT employees.id, employees.first_name, orders.order_id
FROM employees
CROSS JOIN orders
LEFT JOIN orders ON employees.id = orders.employee_id;
```

This query will return all possible combinations of rows from the `employees` table and the `orders` table, including all records from the `employees` table even if there are no matching records in the `orders` table.

### NATURAL JOIN

The `NATURAL JOIN` keyword is used to join two tables based on the columns with the same name and data type in both tables. It automatically matches the columns between the tables. Here is an example:

```sql
SELECT employees.id, employees.first_name, orders.order_id
FROM employees
NATURAL JOIN orders;
```

### Non-ANSI Join Formats

#### Equi Join

An equi join is a type of join that combines rows from two or more tables based on a condition that the values in the columns being joined are equal. Here is an example of an equi join between the `employees` and `orders` tables:

```sql
SELECT employees.id, employees.first_name, orders.order_id
FROM employees, orders
WHERE employees.id = orders.employee_id;
```

#### Non-Equi Join

A non-equi join is a type of join that combines rows from two or more tables based on a condition that is not equality. Here is an example of a non-equi join between the `employees` and `orders` tables:

```sql
SELECT employees.id, employees.first_name, orders.order_id
FROM employees, orders
WHERE employees.id <> orders.employee_id;
```

#### Self Join

A self join is a join in which a table is joined with itself. Here is an example of a self join on the `employees` table:

```sql
SELECT e1.id, e1.first_name, e2.first_name AS manager_name
FROM employees e1, employees e2
WHERE e1.manager_id = e2.id;
```
