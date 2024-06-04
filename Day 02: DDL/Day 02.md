<div align="center">
  <h1> 15 Days Of SQL: Day 1 - Data Definition Language (DDL)</h1>
<sub>Author:
<a href="https://github.com/PythonCode9" target="_blank">Python Coder</a><br>
<small> Second Edition: July, 2024</small>
</sub></div>

[<< Day 01](https://github.com/PythonCode9/15-Days-of-SQL/blob/main/Day%2001%3A%20Basic%20SQL%20Syntax/Day%2001.md)
[Day 03 >>](https://github.com/PythonCode9/15-Days-of-SQL/blame/284988e4491e39111be9b4d22161e06ffa85a61d/Day%2002%3A%20DDL/Day%2002.md)
- [📘 Day 2](#day-02)
  - [Create Table](#)
  - [Drop Table](#)
  - [Alter Table](#)
      - [ADD COLUMN](#)
      - [ADD COLUMNS](#)
      - [DROP COLUMN]()
      - [DROP COLUMNS]()
      - [MODIFY COLUMN]()
      - [ADD Constraints]()
      - [DROP Constraints]()
      - [DROP PRIMARY KEY]()
  - [Truncate Table](#)
  - [Rename Table]()
  - [💻 Exercises: Day 1](#-exercises---day-1)
    - [Exercises: Level 1](#exercises-level-1)
    - [Exercises: Level 2](#exercises-level-2)
   


# 📘Day 02
## Create TABLE
The CREATE TABLE statement in SQL is a Data Definition Language (DDL) command used to create a new table in the database.
#### SQL CREATE TABLE Syntax
The syntax for SQL CREATE TABLE is as follows:
```sql
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    column3 datatype,
   ....
);
```
* table_name is the name of the table that you want to create.
* column1, column2,... are the columns in the table.
* datatype is the data type for the column, such as varchar, int, date, etc.

#### SQL CREATE TABLE Example
Here is an example of the CREATE TABLE statement:
``` sql
CREATE TABLE Employees (
    ID int,
    Name varchar(255),
    Salary int,
    Department varchar(255),
    Position varchar(255)
);
```
This SQL command creates a new table named Employees with five columns, named ‘ID’, ‘Name’, ‘Salary’, ‘Department’, and ‘Position’. The data types are int for the ‘ID’ and ‘Salary’, and varchar(255) for the others.

#### SQL CREATE TABLE with NOT NULL
The NOT NULL constraint enforces a column to not accept null values. When creating a new table, you can add this constraint. Here is a practical example:
CREATE TABLE Employees (
    ID int NOT NULL,
    Name varchar(255) NOT NULL,
    Salary int,
    Department varchar(255),
    Position varchar(255)
);
In the example above, the ‘ID’ and ‘Name’ must always have a value. They cannot be unassigned or undefined.


