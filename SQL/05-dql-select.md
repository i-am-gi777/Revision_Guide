# DQL Commands (Data Query Language)

The Data Query Language (DQL) is used to fetch data from a database. The primary command in this category is:

# Syntax:

```sql
--CREATE TABLE
CREATE TABLE employees (
    emp_id INT PRIMARY KEY,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    email VARCHAR(100),
    phone_number VARCHAR(20),
    hire_date DATE,
    job_title VARCHAR(50),
    salary DECIMAL(10, 2),
    department VARCHAR(50)
);

--INSERT 
INSERT INTO employees (emp_id, first_name, last_name, email, phone_number, hire_date, job_title, salary, department)
VALUES
(1, 'John', 'Doe', 'john.doe@example.com', '555-1234', '2020-01-15', 'Software Engineer', 70000.00, 'IT'),
(2, 'Jane', 'Smith', 'jane.smith@example.com', '555-5678', '2019-03-10', 'HR Manager', 80000.00, 'HR'),
(3, 'Michael', 'Brown', 'michael.brown@example.com', '555-8765', '2021-07-22', 'Data Analyst', 65000.00, 'Analytics'),
(4, 'Emily', 'Davis', 'emily.davis@example.com', '555-4321', '2018-11-05', 'Project Manager', 90000.00, 'Management');

--SELECT
The `SELECT` statement is used to **query data** from one or more tables.
--1. Select All Columns
SELECT * FROM employees;
--2. Select Specific Columns
SELECT first_name, last_name FROM employees;
--3.WHERE Clause: Filters rows based on a condition.
SELECT * FROM employees
WHERE department = 'Sales';
--Operators:
=, !=, <, >, <=, >=
BETWEEN, LIKE, IN, IS NULL, NOT NULL
--4. ORDER BY Clause: Sorts the result set by one or more columns.
--NOTE: ASC = ascending (default),DESC = descending
DESC = descending
SELECT * FROM employees
ORDER BY salary DESC;
--5.GROUP BY Clause: Groups rows sharing the same values in specified columns, often used with aggregate functions.
SELECT department, COUNT(*) AS total_employees
FROM employees
GROUP BY department;
--6.HAVING Clause: Filters groups after GROUP BY.
--NOTE: HAVING is like WHERE, but used for groups.
SELECT department, AVG(salary) AS avg_salary
FROM employees
GROUP BY department
HAVING AVG(salary) > 50000;
--7.DISTINCT Keyword: Removes duplicate values from the result set.
SELECT DISTINCT department FROM employees;
--8.LIMIT (or TOP): Used to limit the number of rows returned.
SELECT * FROM employees
LIMIT 5;
--or
SELECT TOP 5 * FROM employees;
--Combining Clauses
SELECT department, COUNT(*) AS total
FROM employees
WHERE salary > 50000
GROUP BY department
HAVING COUNT(*) > 3
ORDER BY total DESC
LIMIT 5;





