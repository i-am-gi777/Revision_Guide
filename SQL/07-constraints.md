# SQL Constraints

Constraints are rules enforced on data columns in a table. They ensure the accuracy, reliability, and integrity of the data in the database.

Constraints can be applied at two levels:
- **Column-level** (applied to a single column)
- **Table-level** (applied to multiple columns)


##  Common SQL Constraints:
`PRIMARY KEY` :Uniquely identifies each row in a table    
`FOREIGN KEY`  : Enforces a link between two tables        
`NOT NULL`     :Ensures a column cannot have `NULL` values 
`UNIQUE`       :Ensures all values in a column are different
`CHECK` :Ensures all values in a column satisfy a specific condition
`DEFAULT`  :Assigns a default value if no value is provided



# Example:
```sql
-- PRIMARY KEY:
--Uniquely identifies each record in a table.
--Automatically implies `NOT NULL` and `UNIQUE`.
CREATE TABLE students (
    student_id INT PRIMARY KEY,
    name VARCHAR(100)
);

--FOREIGN KEY:
--Enforces referential integrity between two tables.
--Must match a PRIMARY KEY or UNIQUE in another table.
CREATE TABLE enrollments (
    enrollment_id INT PRIMARY KEY,
    student_id INT,
    FOREIGN KEY (student_id) REFERENCES students(student_id)
);
--NOT NULL:
--Ensures that a column cannot have NULL values.
CREATE TABLE products (
    product_id INT,
    product_name VARCHAR(100) NOT NULL
);

--UNIQUE:
--Ensures that all values in a column are different.
CREATE TABLE users (
    user_id INT,
    email VARCHAR(255) UNIQUE
);
--CHECK:
--Validates that values in a column meet a specific condition.
CREATE TABLE employees (
    id INT,
    age INT CHECK (age >= 18)
);
--Can be used on multiple columns too:
CHECK (salary > 0 AND age >= 18)
--DEFAULT:
--Sets a default value if no value is provided during insert.
CREATE TABLE orders (
    id INT,
    status VARCHAR(20) DEFAULT 'Pending'
);
-- Add NOT NULL
ALTER TABLE users
MODIFY email VARCHAR(255) NOT NULL;

-- Add UNIQUE
ALTER TABLE users
ADD CONSTRAINT unique_email UNIQUE (email);

-- Add FOREIGN KEY
ALTER TABLE enrollments
ADD CONSTRAINT fk_student FOREIGN KEY (student_id)
REFERENCES students(student_id);
