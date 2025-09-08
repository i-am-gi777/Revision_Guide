# SQL JOINS

SQL **JOINs** are used to **combine rows** from two or more tables based on a related column between them.

# Types of Joins in SQL


`INNER JOIN`   :Returns matching rows from both tables                             
`LEFT JOIN`  :All rows from the left table + matching rows from the right table  
`RIGHT JOIN`  : All rows from the right table + matching rows from the left table  
`FULL JOIN`   : All rows from both tables (matched + unmatched)                    
`SELF JOIN` : A table joined with itself                                         
`CROSS JOIN`  : Cartesian product (all combinations)                               

# Sample Tables

# `employees`
| emp_id | name    | dept_id |
|--------|---------|---------|
| 1      | Alice   | 101     |
| 2      | Bob     | 102     |
| 3      | Carol   | NULL    |

# `departments`
| dept_id | dept_name     |
|---------|----------------|
| 101     | HR             |
| 102     | IT             |
| 103     | Marketing      |





```sql
--CREATE:
create table employees(
    emp_id int,
    name text,
    dept_id int
);

--INSERT:
insert into employees(emp_id, name, dept_id)values
(1,"Alice", 101),
(2,"Bob",102),
(3,"Carol",NULL);

# `departments`
--CREATE:
create table departments (
     dept_id INT,
      dept_name text
);
--INSERT:
insert into departments (dept_id,  dept_name) values
(101, 'HR'),
(102, 'IT'),
(103, 'Marketing');


--1. INNER JOIN:
--Returns only the **matching rows**.
SELECT e.name, d.dept_name
FROM employees e
INNER JOIN departments d
ON e.dept_id = d.dept_id;
--2. LEFT JOIN:
--Returns all rows from the left table + matching rows from the right.
SELECT e.name, d.dept_name
FROM employees e
LEFT JOIN departments d
ON e.dept_id = d.dept_id;
--3. RIGHT JOIN
--Returns all rows from the right table + matching rows from the left.
SELECT e.name, d.dept_name
FROM employees e
RIGHT JOIN departments d
ON e.dept_id = d.dept_id;
--4. FULL JOIN
--Returns all rows from both tables — matched and unmatched.
SELECT e.name, d.dept_name
FROM employees e
FULL JOIN departments d
ON e.dept_id = d.dept_id;
--5. SELF JOIN
--Joining a table with itself.
SELECT A.name AS Employee, B.name AS Manager
FROM employees A
JOIN employees B ON A.manager_id = B.emp_id;
--6. CROSS JOIN
--Returns the Cartesian product of both tables
SELECT e.name, d.dept_name
FROM employees e
CROSS JOIN departments d;
