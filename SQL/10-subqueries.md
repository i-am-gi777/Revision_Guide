# 🔍 SQL Subqueries

A **subquery** (also called an **inner query** or **nested query**) is a query **inside another query**.

Subqueries help break complex logic into smaller, readable parts.


## 📌 Where Can You Use Subqueries?

| Use Case                  | Example Location         |
|---------------------------|--------------------------|
| Inside `SELECT`           | Return computed values   |
| Inside `FROM`             | Treat subquery as a table|
| Inside `WHERE` / `HAVING` | Filter based on results  |
| Inside `EXISTS`           | Check for row existence  |




```sql
--1. Subquery in `SELECT`
--Use subquery to return a **calculated value**.
SELECT 
  name,
  (SELECT AVG(salary) FROM employees) AS avg_salary
FROM employees;

--2. Subquery in WHERE (Single Value)
--Compare against a single value returned by subquery
SELECT name, salary
FROM employees
WHERE salary > (
  SELECT AVG(salary) FROM employees
);
--3. Subquery in WHERE (Multiple Values)
--Use IN to compare against a list of values.
SELECT name
FROM employees
WHERE dept_id IN (
  SELECT dept_id FROM departments WHERE location = 'New York'
);
--4. Subquery in FROM (Inline View)
--Use subquery as a temporary table.
SELECT dept_id, AVG(salary) AS avg_salary
FROM (
  SELECT dept_id, salary FROM employees
) AS dept_salaries
GROUP BY dept_id;
--5. EXISTS with Subquery
--Check if any rows exist in subquery.
SELECT name
FROM employees e
WHERE EXISTS (
  SELECT 1 FROM projects p WHERE p.emp_id = e.emp_id
);
--6. Correlated Subquery
--A subquery that references outer query columns.
SELECT name, salary
FROM employees e
WHERE salary > (
  SELECT AVG(salary) 
  FROM employees 
  WHERE dept_id = e.dept_id
);
--Real-World Example
SELECT name, dept_id, salary
FROM employees e
WHERE salary = (
  SELECT MAX(salary)
  FROM employees
  WHERE dept_id = e.dept_id
);
