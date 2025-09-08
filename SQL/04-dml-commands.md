# DML Commands (Data Manipulation Language)

DML commands are used to manipulate data within existing tables. They allow you to insert, update, delete, and retrieve data.



# Syntax:

```sql
--CREATE TABLE
CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    salary DECIMAL(10, 2)
);

--INSERT:
--The `INSERT` command adds new rows (records) into a table
INSERT INTO employees (id, name, salary)
VALUES (1, 'Alice', 60000), (2,'BOB',70000);

--UPDATE:
--The 'UPDATE' command modifies existing data in a table
UPDATE employees
SET salary = 65000
WHERE id = 1;

--DELETE
--The 'DELETE' command removes rows from a table.
--Warning: Without a WHERE clause, all rows will be deleted.
DELETE FROM employees
WHERE id = 1;


