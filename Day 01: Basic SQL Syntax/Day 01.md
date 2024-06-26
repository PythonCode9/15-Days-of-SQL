<div align="center">
  <h1> 15 Days Of SQL: Day 1 - Basic SQL Syntax</h1>
<sub>Author:
<a href="https://github.com/PythonCode9" target="_blank">Python Coder</a><br>
<small> Second Edition: July, 2024</small>
</sub></div>

[Day 02 >>](https://github.com/PythonCode9/15-Days-of-SQL/blame/284988e4491e39111be9b4d22161e06ffa85a61d/Day%2002%3A%20DDL/Day%2002.md)
- [📘 Day 1](#day-01)
  - [Introduction](#introduction)
    - [SQL](#sql)
    - [Relational Databases](#relational-databases)
    - [Relationships](#relationships)
    - [SQL Databases](#sql-databases)
      - [Advantages of SQL Databases](#advantages-of-sql-databases)
      - [Limitations of SQL Databases](#limitations-of-sql-databases)
  - [SQL Keywords](#basic-sql-keywords)
  - [Data Types](#data-types)
  - [Operators](#operators)
    - [Expression Operators](#expression-operators)
    - [Advanced Operators](#advanced-operators)
  - [Statements](#statements)
    - [SELECT](#select-retrieving-specific-data)
    - [INSERT](#insert-adding-new-data)
    - [UPDATE](#update-modifying-existing-data)
    - [DELETE](#delete-removing-data)
  - [💻 Exercises: Day 1](#-exercises---day-1)
    - [Exercises: Level 1](#exercises-level-1)
    - [Exercises: Level 2](#exercises-level-2)











# 📘Day 01
## Introduction:

### SQL

SQL, which stands for Structured Query Language, is a programming language used to communicate with and manage databases. It's a standard language for manipulating data held in relational database management systems (RDBMS) or for stream processing in a relational data stream management system (RDSMS).  SQL was first developed by IBM in the 1970s.

### Relational Databases

A relational database is a type of database that stores and organizes data in a structured way:

* It uses a structure that allows data to be identified and accessed in relation to other data in the database.
* Data is stored in various data tables, each with a unique key identifying every row.
* Relational databases are made up of sets of tables with data that fits into predefined categories. Each table has at least one data category in a column, and each row contains a specific data instance for the categories defined in the columns.

**Example:**

| EmployeeID | FirstName | LastName  | Email                 |
|-----------|------------|-----------|------------------------|
| 1          | Celeste    | Moon       | Celeste.Moon@example.com |
| 2          | Dustin     | Blake      | Dustin.Blake@example.com  |
| 3          | Emory      | Lane       | Emory.Lane@example.com   | 

### Relationships

The term "relational database" comes from the concept of a relation—a set of tuples that the database organizes into rows and columns. Each row in a table represents a relationship among a set of values.

**Example:**

| OrderID | EmployeeID | Product      |
|---------|------------|--------------|
| 1        | 3          | Apples        |
| 2        | 1          | Peaches       |
| 3        | 2          | Cherries      |

### SQL Databases

SQL (Structured Query Language) databases are also known as relational databases. They have a predefined schema, and data is stored in tables consisting of rows and columns. SQL databases follow the ACID (Atomicity, Consistency, Isolation, Durability) properties to ensure reliable transactions. Some popular SQL databases include MySQL, PostgreSQL, and Microsoft SQL Server.

#### Advantages of SQL Databases

* **Predefined schema:** Ideal for applications with a fixed structure.
* **ACID transactions:** Ensures data consistency and reliability.
* **Support for complex queries:** Rich SQL queries can handle complex data relationships and aggregation operations.
* **Scalability:** Vertical scaling by adding more resources to the server (e.g., RAM, CPU).

#### Limitations of SQL Databases

* **Rigid schema:** Data structure updates are time-consuming and can lead to downtime.
* **Scaling:** Difficulties in horizontal scaling and sharding of data across multiple servers.
* **Not well-suited for hierarchical data:** Requires multiple tables and JOINs to model tree-like structures.

## Basic SQL Keywords

SQL employs a number of standard command keywords that are integral to interacting with databases. Keywords in SQL provide instructions as to what action should be performed. Here are some of the primary SQL keywords:

* **SELECT:** This keyword retrieves data from a database.
    * **Example:**
    ```sql
    SELECT * FROM Customers;
    ```
    In the above statement, `*` indicates that all records should be retrieved from the `Customers` table.

* **FROM:** This keyword tells you exactly where to look for the data you want in your database.
    * **Example:**
    ```sql
    SELECT * FROM Customers WHERE Country='America';
    ```

* **INSERT INTO:** This command is used to insert new data into a database.
    * **Example:**
    ```sql
    INSERT INTO Customers (CustomerID, CustomerName, ContactName, Address, City, PostalCode, Country)
    VALUES ('Cardinal','Tom B. Erichsen','Skagen 21','Stavanger','4006','Norway');
    ```

* **UPDATE:** This keyword updates existing data within a table.
    * **Example:**
    ```sql
    UPDATE Customers SET ContactName='Alfred Schmidt', City='Frankfurt' WHERE CustomerID=1;
    ```

* **DELETE:** This command removes one or more records from a table.
    * **Example:**
    ```sql
    DELETE FROM Customers WHERE CustomerName='Alfreds Futterkiste';
    ```

## Data Types

SQL data types define the type of data that can be stored in a database table's column. Depending on the DBMS, the names of the data types can differ slightly. Here are the general types:

* **INT:** Used for whole numbers.
    * **Example:**
    ```sql
    CREATE TABLE Employees (
        ID INT,
        Name VARCHAR(30)
    );
    ```

* **DECIMAL:** Used for decimal and fractional numbers.
    * **Example:**
    ```sql
    CREATE TABLE Items (
        ID INT,
        Price DECIMAL(5,2)
    );
    ```

* **CHAR:** Used for fixed-length strings.
    * **Example:**
    ```sql
    CREATE TABLE Employees (
        ID INT,
        Initial CHAR(1)
    );
    ```

* **VARCHAR:** Used for variable-length strings.
    * **Example:**
    ```sql
    CREATE TABLE Employees (
        ID INT,
        Name VARCHAR(30)
    );
    ```

* **DATE:** Used for dates in the format (YYYY-MM-DD).
    * **Example:**
    ```sql
    CREATE TABLE Employees (
        ID INT,
        BirthDate DATE
    );
    ```

* **DATETIME:** Used for date and time values in the format (YYYY-MM-DD HH:MI:SS).
    * **Example:**
    ```sql
    CREATE TABLE Orders (
        ID INT,
        OrderDate DATETIME
    );
    ```

* **BINARY:** Used for binary strings.

* **BOOLEAN:** Used for boolean values (TRUE or FALSE).

Remember, the specific syntax for creating tables and defining column data types can vary slightly depending on the SQL database you are using (MySQL, PostgreSQL, SQL Server, SQLite, Oracle, etc.), but the general concept and organization of data types is cross-platform.


## Operators

SQL operators are used to perform operations like comparisons and arithmetic calculations. They are crucial for forming queries. SQL operators are divided into the following types:

### Expression Operators

* **Arithmetic Operators:** These are used to perform mathematical operations. Here's a list:
    * `+`: Addition
    * `-`: Subtraction
    * `*`: Multiplication
    * `/`: Division
    * `%`: Modulus

    * **Example:**
    ```sql
    SELECT product, price, (price * 0.18) as tax
    FROM products;
    ```

* **Comparison Operators:** These are used in the WHERE clause to compare one expression with another. Some examples:
    * `=`: Equal
    * `!=` or `<>`: Not equal
    * `>`: Greater than
    * `<`: Less than
    * `>=`: Greater than or equal
    * `<=`: Less than or equal

    * **Example:**
    ```sql
    SELECT name, age
    FROM students
    WHERE age > 18;
    ```

* **Logical Operators:** They are used to combine the result set of two different component conditions. These include:
    * `AND`: Returns true if both components are true.
    * `OR`: Returns true if any one of the components is true.
    * `NOT`: Returns the opposite boolean value of the condition.

    * **Example:**
    ```sql
    SELECT *
    FROM employees
    WHERE salary > 50000 AND age < 30;
    ```

* **Bitwise Operators:** These perform bit-level operations on the inputs. Here's a list:
    * `&`: Bitwise AND
    * `|`: Bitwise OR
    * `^`: Bitwise XOR

    Bitwise operators are much less commonly used in SQL than the other types of operators.

Remember, the data type of the result depends on the types of the operands.

### Advanced Operators

## Statements
### SELECT: Retrieving Specific Data

The `SELECT` statement is used in SQL to pick out specific data from a database. In other words, it's used to select from the database what you want to display. The syntax for the `SELECT` statement is fairly straightforward:
```sql
SELECT column(s)
FROM table
WHERE condition;
```
**Explanation:**
* `column(s)`: Enter the name(s) of the column(s) you want to display, separated by commas.
* `table`: The name of the table from which you want to retrieve data.
* `WHERE (Optional)`: This clause filters the results based on a specified condition. It allows you to select only rows that meet certain criteria.
          
* **Selecting All Columns:**
For instance, if you wanted to select all data from the “Customers” table, your query would look like this:
```sql
SELECT *
FROM Customers;
```
In the above code, the asterisk * denotes “all”. This will retrieve all of the data in the “Customers” table.
* **Selecting Specific Columns:**
Selecting Specific Columns: You can choose specific columns instead of all by listing their names after `SELECT`.
```sql
SELECT FirstName, LastName
FROM Customers;
```
* **WHERE Clause:**
You can also filter using the WHERE clause. For example, selecting only the customers who are from “America”:
```sql
SELECT *
FROM Customers
WHERE Country='America';
```
* **ORDER BY Clause:**
Sorting with ORDER BY: Use the `ORDER BY` clause to sort the retrieved data:
* `ORDER BY`: Sorts results in ascending order.
* `ORDER BY DESC`: Sorts results in descending order.
```sql
SELECT *
FROM Customers
ORDER BY Country;  -- Ascending order
```
These are the very basics of the SELECT statement in SQL, which is a vital part of working with databases.

### INSERT: Adding New Data

The `INSERT` statement is used to add new rows of data to a table. It comes in three main forms:

* `INSERT INTO values`
* `INSERT INTO set`
* `INSERT INTO select`

* **INSERT INTO VALUES:**

This form specifies both the column names and the values to be inserted:

```sql
INSERT INTO table_name (column1, column2, column3, ...)
VALUES (value1, value2, value3, ...);
```

* **INSERT INTO SET:**

This form uses the `SET` keyword to specify each column and its corresponding value:

```sql
INSERT INTO table_name
SET column1 = value1, column2 = value2, ...;
```

* **INSERT INTO SELECT:**

This form allows you to copy data from another table:

```sql
INSERT INTO table_name1 (column1, column2, column3, ...)
SELECT column1, column2, column3, ...
FROM table_name2
WHERE condition;
```

**Important Note:** When inserting data, columns with default values don't need to be included in the `INSERT INTO` statement. However, be cautious as SQL doesn't have a confirmation step. Once you execute the insert, the data is added permanently.


### UPDATE: Modifying Existing Data

The `UPDATE` statement allows you to modify existing data within a database table. It's a powerful tool when you need to change specific values in existing rows. Here's the syntax:

```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```

* **Explanation:**

* `table_name`: The name of the table where the update will occur.
* `SET`: This clause specifies the columns being updated and their new values.
* `column1, column2, ...`: The names of the columns to be updated.
* `value1, value2, ...`: The new values to be assigned to the respective columns.
* `WHERE`: This clause defines the conditions for selecting the rows to be updated.

* **Example:**

Consider an "Employees" table:

| EmployeeID | Name      | Position | Salary |
|-----------|-----------|-----------|--------|
| 1          | Celeste   | Manager   | 50000  |
| 2          | Dustin    | Clerk     | 30000  |
| 3          | Emory     | Engineer  | 40000  |

To increase Emory's salary (EmployeeID 3) by $5000, you would use the following query:

```sql
UPDATE Employees
SET Salary = Salary + 5000
WHERE EmployeeID = 3;
```

This would permanently update the "Employees" table:

| EmployeeID | Name      | Position | Salary |
|-----------|-----------|-----------|--------|
| 1          | Celeste   | Manager   | 50000  |
| 2          | Dustin    | Clerk     | 30000  |
| 3          | Emory     | Engineer  | 45000  |

* **Caution:** Be mindful when using the `UPDATE` statement. If you omit the `WHERE` clause, all rows in the table will be updated!


### DELETE: Removing Data

The `DELETE` statement allows you to remove existing records from a database table. It's a destructive operation, so use it with caution as it permanently removes data. Here's what you can achieve with `DELETE`:

* **Delete All Rows:**

The `DELETE` statement without a `WHERE` clause removes all rows from a table. This action is irreversible.

```sql
DELETE FROM table_name;
```

This statement deletes all records from the specified `table_name`.

* **Delete Specific Rows:**

Combine the `DELETE` statement with the `WHERE` clause to target specific rows based on a condition.

```sql
DELETE FROM table_name
WHERE condition;
```

This example removes records from `table_name` that meet the specified `condition`.

* **Important Note:** Use `DELETE` cautiously. It can potentially erase important rows or even empty an entire table. The deletion made by `DELETE` is permanent and cannot be undone. Always ensure you have a backup before running a `DELETE` query, especially on a production database.





## 💻 Exercises - Day 1
### Exercises: Level 1
1. Consider the following table named Customers:

| CustomerID | CustomerName| City |
|------------|-------------|----------|
| 1          | Celeste     | New York   |
| 2          | Dustin      | London   |
| 3          | Emory       | Paris | 

Write a query to:
* What are the names of every customer?
* Who are the customers that live in New York City?

2. Write a query to display the customer names and their corresponding cities.

### Exercises: Level 2

1. Create a new table named Products with columns for ProductID (integer), ProductName (text), and Price (decimal).

2. Insert a few sample products into the Products table.

3. Write a query to select all products with a price greater than $10.

4. Write a query to find the most expensive product in the database. (Hint: Use an aggregate function)

These exercises will help you practice the basic building blocks of SQL syntax. There are many online resources and tutorials available for further practice!

🎉 CONGRATULATIONS ! 🎉

