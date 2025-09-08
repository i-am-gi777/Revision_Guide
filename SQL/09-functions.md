# 🔧 SQL Functions

SQL functions are **built-in operations** that perform calculations, format data, or manipulate values in your queries.


# Categories of SQL Functions


Aggregate Functions  : Perform calculations on multiple rows   
Scalar Functions   :Operate on a single value               
String Functions   :Manipulate text values                  
Date Functions     : Work with dates and times               
Conversion Functions :Convert data types                     
Math Functions     : Perform mathematical operations      


```sql
--1. Aggregate Functions

--Operate on **multiple rows** and return a **single result**.

--| Function     | Description                          |
--|--------------|--------------------------------------|
--| `COUNT()`    | Total number of rows                 |
--| `SUM()`      | Total of numeric column              |
--| `AVG()`      | Average value                        |
--| `MIN()`      | Smallest value                       |
--| `MAX()`      | Largest value                        |
SELECT COUNT(*) FROM orders;

SELECT AVG(salary) FROM employees;

-- 2. Scalar Functions:
--Operate on single values, return one result per row.

--UPPER(text)	   Convert to uppercase
--LOWER(text)	   Convert to lowercase
--LENGTH(text)   Get length of string
--ROUND(num, 2)  Round number to 2 decimal places

SELECT UPPER('sql functions');  -- Output: SQL FUNCTIONS

--3. String Functions:
--`CONCAT(a, b)`   : Combine strings                
--`SUBSTRING(text, start, length)`: Extract part of string        
--`TRIM(text)`     :Remove leading/trailing spaces 
--`REPLACE(text, from, to)`   : Replace text             
SELECT CONCAT(first_name, ' ', last_name) AS full_name FROM users;
--4. Date Functions
--| Function                    | Description                |
--| --------------------------- | -------------------------- |
--| `CURRENT_DATE`              | Today's date               |
--| `CURRENT_TIMESTAMP`         | Current date and time      |
--| `DATE_PART('year', date)`   | Extract year               |
--| `DATE_TRUNC('month', date)` | Truncate to first of month |
--| `AGE(NOW(), birth_date)`    | Calculate age              |

SELECT CURRENT_DATE;
SELECT DATE_PART('year', order_date) FROM orders;

--5. Conversion Functions
--| Function              | Description                  |
--| --------------------- | ---------------------------- |
--| `CAST(value AS type)` | Convert to another data type |
--| `TO_CHAR(date, fmt)`  | Format date to string        |
--| `TO_DATE(text, fmt)`  | Convert string to date       |

SELECT CAST('123' AS INT);
SELECT TO_CHAR(NOW(), 'YYYY-MM-DD');

--6. Math Functions
--| Function      | Description             |
--| ------------- | ----------------------- |
--| `ABS(x)`      | Absolute value          |
--| `CEIL(x)`     | Round up                |
--| `FLOOR(x)`    | Round down              |
--| `POWER(x, y)` | x raised to the power y |
--| `MOD(x, y)`   | Remainder (modulo)      |

SELECT POWER(2, 3); -- Output: 8
SELECT MOD(10, 3);  -- Output: 1

--Real-World Example
SELECT 
  customer_id,
  COUNT(*) AS total_orders,
  SUM(order_total) AS total_spent,
  MAX(order_date) AS last_order_date
FROM orders
GROUP BY customer_id;
