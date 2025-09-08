# DCL & TCL Commands in SQL

This section covers:

- **DCL** (Data Control Language): Used to control access to data.
- **TCL** (Transaction Control Language): Used to manage transactions in the database.



##  DCL – Data Control Language

DCL commands are used to **grant** or **revoke** access permissions to users.



# Syntax:
```sql
-- GRANT:
--Gives a user access privileges to the database.
--NOTE: This allows user1 to perform SELECT and INSERT operations on the employees table.
GRANT SELECT, INSERT
ON employees
TO user1;

-- Revoke:
--Removes previously granted access rights.
REVOKE INSERT
ON employees
FROM user1;

TCL – Transaction Control Language
TCL commands are used to manage transactions — a sequence of operations performed as a single unit of work.

--1.COMMIT
--Saves all changes made during the current transaction.
COMMIT;
--ROLLBACK
--Undoes changes made in the current transaction.
ROLLBACK;
--SAVEPOINT
--Sets a point in a transaction to which you can later roll back.
SAVEPOINT savepoint_name;
--ROLLBACK TO SAVEPOINT
--Reverts the transaction to a previously defined savepoint.
ROLLBACK TO savepoint_name;

BEGIN;

UPDATE accounts SET balance = balance - 500 WHERE id = 1;
UPDATE accounts SET balance = balance + 500 WHERE id = 2;

-- If no errors, commit the transaction
COMMIT;

-- If something goes wrong:
-- ROLLBACK;
