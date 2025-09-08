# DDL Commands (Data Definition Language)

Used to define and modify database structure.


```sql
--CREATE TABLE
create table employees (
    id int,
    name text,
    salary int
    );


--ALTER TABLE
ALTER TABLE employees ADD department text;

--TRUNCATE  TABLE
TRUNCATE TABLE employees; -- Deletes all rows but keeps the employees table

--DROP  TABLE  
DROP TABLE employees; -- Deletes the entire employees table
