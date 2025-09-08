```sql
--CREATE  
create table employees (
    emp_id int,
    name text,
    department text,
    salary int,
    manger_id int
);
--INSERT INTO 
insert into employees (emp_id,name,department, salary,manger_id) values 
(1, "Alice", "HR", 50000, "NULL"),
(2, "Bob", "IT", 70000, 1),
(3, "Charlie", "IT", 65000, 2),
(4, "David","Sales", 60000,1);
--SELECT 
--Select all columns:
select * from employees;
--Select specific columns:
select emp_id,name,manger_id from employees;
--3.WHERE Clause: Filters rows based on a condition.
select * from employees
where department = 'Sales';
--Operators: 
--=, !=, <, >, <=, >=
select * from employees
where department = 'IT';
select * from employees 
where department != 'IT';
select * from employees 
where salry < 650000;
select * from employees 
where salary > 60000;
select * from employees
where salary <= 60000;
select * from employees
where salary >= 650000;
--BETWEEN, LIKE, IN, IS NULL, NOT NULL
select * from employees 
where salary between 60000 and 70000;
select * from employees 
where name like 'A%';
select * from employees 
where name like '%e';
select * from employees
where name like '%a%';
select * from employees
where department  in ('IT', 'Sales');
select * from emplyees 
where manger_id is NULL;
select * from employees
where manger_id is not NULL;
--4. ORDER BY Clause: Sorts the result set by one or more columns.
--ORDER BY
--ASC,DESC
--NOTE: ASC = ascending (default),DESC = descending
DESC = descending
select * from employees
order by salary desc;
select * from employees
order by emp_id asc;
--5.GROUP BY Clause: Groups rows sharing the same values in specified columns, often used with aggregate functions.
select * from employees
group by department;

SELECT department, COUNT(*) AS total_employees
FROM employees
GROUP BY department;
--6.HAVING Clause: Filters groups after GROUP BY.
--NOTE: HAVING is like WHERE, but used for groups.
select * from employees
having department = 'IT';

SELECT department, AVG(salary) AS avg_salary
FROM employees
GROUP BY department
HAVING AVG(salary) > 50000;
--7.DISTINCT Keyword: Removes duplicate values from the result set.
select distinct department from employees;
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
--UPDATE,ROWID 
update employees set salary = 75000 where name = 'Bob';
select ROWID, * from employees;
--DELETE 
delete from employees where name = 'David';
--ALTER 
alter table employees add email text;
alter table employees  manger_id to manager_id;
--COUNT
select count(*) from employees;
select count(*) from employees where department = 'IT';
--MAX
select max(salary) as highest_salary from employees;
--MIN
select min(salary) as lowest_salary from employees;
--AND
select * from employees w
here department = 'IT' and salary > 50000
--OR
select * from employees w
here department = 'IT' or salary > 50000
--QUERY IN QUERY
select * from employees
where salary > (select avg(salary) from employees);
--A UNION B
create table dept_A(
    emp_id int,
    name text
);
create table dept_B(
    emp_id int,
    name text
);
insert into dept_A values (1, 'Alice'),(2,'Bob');
insert into dept_B values (2, 'Bob'),(3,'Chalie');
select * from dept_A
union
select * from dept_B
--A INTERSECTION B
select * from dept_A
intersect
select * from dept_B
--A MINUS B(EXCEPT)
select * from dept_A
except
select * from dept_B
--JION/INNER JION
create table managers (
    manager_id int
    manager_name text
);
insert into managers values (1, 'm1'),(2,'m2');

select * from employees e
inner join managers m
on e.manager_id =m.manager_id;
--LEFT JION
select * from employees e
left join managers m
on e.manager_id = m.manager_id;
--RIGHT JION
select * from employees e
right join managers m
on e.manager_id = m.manager_id;
--CASE
select name, salary, department,
    case
        when salary >= 60000 then 'high'
        when salary <= 50000 then 'medium'
        else 'low'
    end as salary_band
from employees
--EXISTS
select name from employees e 
where exists (
    select 1 from employees m
    where e.manager_id = m.emp_id
);
--CORRELATED QUERY
select * from employees e
where e.name = (
    select * from employees m
    where e.manager_id = m.emp_id
);
--RANK
select name, salary, departmentrank()over (order by salry desc) as rank_salary 
from employees;
--DENSE RANK
select name, salary, department dense_rank()over (order by salry desc) as dense_rank_salary 
from employees;
--COUNT, SUM, MAX, MIN, AVG
select 
    count(*) as total_emp
    sum(salary) as total_salary
    max(salary) as highest_salary
    min(salary) as lowest_salary
    avg(salary) as avg_salary
from employees;
--PARTITION BY
select name, salary, department
 rank() over (partition by department order by salary desc)as dept_rank from employees;
--DROP
drop table employees