<div align="center">
  <h1> 15 Days Of SQL: Day 2 - Data Definition Language (DDL)</h1>
<sub>Author:
<a href="https://github.com/PythonCode9" target="_blank">Python Coder</a><br>
<small> Second Edition: July, 2024</small>
</sub></div>

[<< Day 01](https://github.com/PythonCode9/15-Days-of-SQL/blob/main/Day%2001%3A%20Basic%20SQL%20Syntax/Day%2001.md)
[Day 03 >>](https://github.com/PythonCode9/15-Days-of-SQL/blame/284988e4491e39111be9b4d22161e06ffa85a61d/Day%2002%3A%20DDL/Day%2002.md)
- [📘 Day 2](#day-02)
  - [Create Table](./#create-table)
  - [Drop Table](./drop-table)
  - [Alter Table](./alter-table)
      - [ADD COLUMN](./add-column)
      - [DROP COLUMN](./drop-column)
      - [MODIFY COLUMN](./modify-column)
      - [ADD/DROP Constraints](./adddrop-constraints)
  - [Truncate Table](./truncate-table)
  - [Rename Table](./rename-table)
  - [💻 Exercises: Day 1](./-exercises---day-2)
    - [Exercises: Level 1](./exercises-level-1)
    - [Exercises: Level 2](./exercises-level-2)
   


# 📘Day 02
# Create Table

The `CREATE TABLE` statement in SQL is a Data Definition Language (DDL) command used to create a new table in the database. 

## SQL CREATE TABLE Syntax

The syntax for SQL `CREATE TABLE` is as follows:

```sql
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    column3 datatype,
   ....
);
```

- `table_name` is the name of the table that you want to create.
- `column1, column2,...` are the columns in the table.
- `datatype` is the data type for the column, such as varchar, int, date, etc.

## SQL CREATE TABLE Example 

Here is an example of the `CREATE TABLE` statement:

```sql
CREATE TABLE Employees (
    ID int,
    Name varchar(255),
    Salary int,
    Department varchar(255),
    Position varchar(255)
);
``` 

This SQL command creates a new table named `Employees` with five columns, named 'ID', 'Name', 'Salary', 'Department', and 'Position'. The data types are int for the 'ID' and 'Salary', and varchar(255) for the others.

## SQL CREATE TABLE with NOT NULL 

The `NOT NULL` constraint enforces a column to not accept null values. When creating a new table, you can add this constraint. Here is a practical example:

```sql
CREATE TABLE Employees (
    ID int NOT NULL,
    Name varchar(255) NOT NULL,
    Salary int,
    Department varchar(255),
    Position varchar(255)
);
```

In the example above, the 'ID' and 'Name' must always have a value. They cannot be unassigned or undefined.

# Drop Table

The `DROP TABLE` statement is a Data Definition Language (DDL) operation that is used to completely remove a table from the database. This operation deletes the table structure along with all the data in it, effectively removing the table from the database system.

When you execute the `DROP TABLE` statement, it eliminates both the table and its data, as well as any associated indexes, constraints, and triggers. Unlike the `TRUNCATE TABLE` statement, which only removes data but keeps the table structure, `DROP TABLE` removes everything associated with the table.

## Syntax

In SQL, the `DROP TABLE` statement is quite simple:

```sql
DROP TABLE table_name;
```

In this command, "table_name" refers to the name of the table you wish to remove.

## Example

If you have a table named `Orders` and you want to delete the entire table, you would use:

```sql
DROP TABLE Orders;
```

After executing this statement, the `Orders` table would no longer exist in the database.

## Considerations

- **Irreversible Action**: Unlike `DELETE` and `TRUNCATE`, once a table is dropped, the action cannot be rolled back. Therefore, it should be used with extreme caution.
- **Cascading Effects**: Dropping a table that is referenced by a foreign key constraint will also drop that foreign key relationship. Similarly, any dependent objects like views, stored procedures, or functions that reference the table might be affected.
- **Permissions**: Ensure you have the appropriate permissions to drop the table. Typically, this requires `DROP` privilege on the table.

## Limitations

There are certain conditions and limitations to keep in mind when using `DROP TABLE`:

- **Foreign Key Constraints**: If the table is referenced by foreign keys from other tables, dropping it might require using `CASCADE` to also drop the dependent foreign keys.
- **Replication**: Tables published using transactional or merge replication should be carefully considered before dropping, as this can impact replication.
- **Dependent Objects**: Dropping a table will invalidate any dependent objects such as views, stored procedures, and functions that reference the table. Ensure these are handled appropriately.

For example, if a table `Orders` is referenced by a foreign key in another table `OrderDetails`, dropping `Orders` might require:

```sql
DROP TABLE Orders CASCADE;
```

This ensures that any foreign key relationships are also removed along with the table.

# Alter Table

The `ALTER TABLE` command in SQL is used to add, delete/drop, or modify columns in an existing table. It's also useful for adding and dropping constraints such as primary key, foreign key, etc. 

## Add Column

A single column can be added using the following syntax:

```sql
ALTER TABLE tableName
ADD columnName datatype;
```

To add more than one column:

```sql
ALTER TABLE tableName
ADD (columnName1 datatype,
     columnName2 datatype,
     ...
     );
```

## Drop Column

To drop a single column:

```sql
ALTER TABLE tableName
DROP COLUMN columnName;
```

To drop multiple columns:

```sql
ALTER TABLE tableName
DROP (columnName1,
       columnName2,
       ...
      );
```

## Modify Column

To modify the datatype of a column:

```sql
ALTER TABLE tableName
MODIFY COLUMN columnName newDataType;
```

## Add/Drop Constraints

To add constraints:

```sql
ALTER TABLE tableName
ADD CONSTRAINT constraintName
PRIMARY KEY (column1, column2, ... column_n);
```

To drop constraints:

```sql
ALTER TABLE tableName
DROP CONSTRAINT constraintName;
```

To drop PRIMARY KEY:

```sql
ALTER TABLE table_name
DROP PRIMARY KEY;
```
In conclusion, `ALTER TABLE` in SQL lets you alter the structure of an existing table. This is a powerful command that lets you dynamically add, modify, and delete columns as well as the constraints placed on them. It ensures you are more flexible in dealing with changing data storage requirements.

# Truncate Table

The `TRUNCATE TABLE` statement is a Data Definition Language (DDL) operation that is used to mark the extents of a table for deallocation (empty for reuse). The result of this operation quickly removes all data from a table, typically bypassing a number of integrity enforcing mechanisms intended to protect data (like triggers).

It effectively eliminates all records in a table, but not the table itself. Unlike the `DELETE` statement, `TRUNCATE TABLE` does not generate individual row delete statements, so the usual overhead for logging or locking does not apply.

## Syntax

In SQL, the `TRUNCATE TABLE` statement is quite simple:

```sql
TRUNCATE TABLE table_name;
```

In this command, "table_name" refers to the name of the table you wish to clear.

## Example

If you have a table named `Orders` and you want to delete all its records, you would use:

```sql
TRUNCATE TABLE Orders;
```

After executing this statement, the `Orders` table would still exist, but it would be empty.

Remember, while `TRUNCATE TABLE` is faster and uses fewer system and transaction log resources than `DELETE`, it does not invoke triggers and cannot be rolled back, so use with caution.

## Limitations

Truncate preserves the structure of the table for future use. But you can't truncate a table that:

- Is referenced by a FOREIGN KEY constraint. (You can truncate a table that has a foreign key that references itself.)
- Participates in an indexed view.
- Is published by using transactional replication or merge replication.

If you try to truncate a table with a foreign key constraint, SQL Server will prevent you from doing so and you will have to use the `DELETE` statement instead.

For partitioned tables, `TRUNCATE TABLE` removes all rows from all partitions. The operation is not allowed if the table contains any LOB columns - `varchar(max), nvarchar(max), varbinary(max), text, ntext, image, xml`, or if the table contains any filestream columns or spatial geo, geography, geometry, and hierarchyid data type columns, or any columns of CLR user-defined data types.


# Rename Table
This is used to rename an object in the database.
### Example
```sql
-- To rename a table
ALTER TABLE table_name
RENAME TO new_table_name;
    
-- To rename a column
ALTER TABLE table_name
RENAME COLUMN old_column_name TO new_column_name;
```


## 💻 Exercises - Day 2
### Exercises: Level 1
1. Create a table named Customers with the following columns:

- customer_id `INT PRIMARY KEY`
- name `VARCHAR(255) NOT NULL`
- email `VARCHAR(255) UNIQUE`
- phone_number `CHAR(10)`

2. Write a SQL statement to add a new column named city (VARCHAR(50)) to the Customers table.

3. Write a SQL statement to modify the data type of the phone_number column in the Customers table to VARCHAR(15).

4. Explain the difference between the DROP TABLE and TRUNCATE TABLE statements.

5. Write a SQL statement to rename the Customers table to ClientList.

### Exercises: Level 2
1. Create a table named Products with the following columns:

- product_id `INT PRIMARY KEY AUTO_INCREMENT`
- name `VARCHAR(255) NOT NULL`
- price `DECIMAL(10,2)`
- description `TEXT`

2. Write a SQL statement to delete all rows from the Products table without removing the table structure itself.

3. Write a SQL statement to add a foreign key constraint to the Products table that references the customer_id column in the Customers table (assuming it exists).

4. Explain why you might not be able to truncate a table with a foreign key constraint.

5. Write a SQL statement to drop the Products table entirely, including the table structure and all data.

These exercises will help you practice the basic building blocks of SQL syntax. There are many online resources and tutorials available for further practice!

🎉 CONGRATULATIONS ! 🎉
