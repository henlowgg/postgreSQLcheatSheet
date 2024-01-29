PostgreSQL Cheat Sheet

A condensed cheat sheet that covers the most essential and commonly used aspects of PostgreSQL, which would be particularly useful for a coding interview. Keep in mind that this cheat sheet will focus on fundamental operations and syntax, and won't cover every possible aspect of PostgreSQL.

Basic Commands
Connect to a Database

SIMPLE TERMINOLOGY AND KEYS

\c dbname
List Databases


\l
List Tables


\dt
Describe Table Structure


\d tablename
Quit psql


\q
Data Definition Language (DDL)
Create Database


CREATE DATABASE dbname;
Drop Database


DROP DATABASE dbname;
Create Table


CREATE TABLE tablename (
    column1 datatype1,
    column2 datatype2,
    ...
);
Drop Table


DROP TABLE tablename;
Alter Table (e.g., Add Column)


ALTER TABLE tablename ADD COLUMN new_column datatype;
Data Manipulation Language (DML)
Insert Data


INSERT INTO tablename (column1, column2, ...) VALUES (value1, value2, ...);
Update Data


UPDATE tablename SET column1 = value1, column2 = value2, ... WHERE condition;
Delete Data


DELETE FROM tablename WHERE condition;
Select Data


SELECT column1, column2, ... FROM tablename WHERE condition;
Data Querying
Filtering

WHERE clause
Logical operators: AND, OR, NOT
Sorting


ORDER BY column [ASC|DESC];
Joining Tables

INNER JOIN
LEFT JOIN
RIGHT JOIN
FULL OUTER JOIN
Aggregation

COUNT, SUM, AVG, MIN, MAX
GROUP BY
HAVING
Subqueries

Used in WHERE, FROM, or SELECT clauses
Advanced Concepts
Indexes

CREATE INDEX
DROP INDEX
Views

CREATE VIEW
DROP VIEW
Transactions

BEGIN TRANSACTION
COMMIT
ROLLBACK
User Management

CREATE ROLE
GRANT
REVOKE
Functions and Stored Procedures

Triggers

Performance Tuning
Explain Plan


EXPLAIN SELECT ...
Index Usage

Query Optimization Techniques

Backup and Restore
Backup Database/Table


pg_dump dbname > outfile
Restore Database/Table


psql dbname < infile


Examples and potential coding challenge questions for each of the PostgreSQL concepts listed in the cheat sheet. These examples and questions will give you a good sense of what you might encounter in a coding interview.

Basic Commands
Example:
Connect to a database named testdb:


\c testdb
Example Question:
How do you list all the tables in the current database using psql command-line tool?

Data Definition Language (DDL)
Example:
Create a table named employees:


CREATE TABLE employees (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    position VARCHAR(100),
    salary DECIMAL
);
Example Question:
Write a SQL command to create a table orders with columns order_id (primary key, integer), order_date (date), and customer_id (integer).

Data Manipulation Language (DML)
Example:
Insert data into the employees table:


INSERT INTO employees (name, position, salary) VALUES ('John Doe', 'Manager', 50000);
Example Question:
Write a SQL command to update the salary of all employees in the employees table to 55000 where the current salary is less than 50000.

Data Querying
Example:
Select employees earning more than 40000 and sort them by name:


SELECT * FROM employees WHERE salary > 40000 ORDER BY name;
Example Question:
How would you write a query to find the average salary of all employees in the employees table, grouped by their position?

Advanced Concepts
Indexes
Example:
Create an index on the salary column in the employees table:


CREATE INDEX idx_salary ON employees (salary);
Example Question:
When would you consider creating an index on a table column, and what are the potential downsides?

Performance Tuning
Example:
Explain the execution plan for a query:


EXPLAIN SELECT * FROM employees WHERE salary > 30000;
Example Question:
What does the EXPLAIN command do in PostgreSQL, and how can it help in optimizing queries?

Backup and Restore
Example:
Backup the testdb database:


pg_dump testdb > testdb_backup.sql
Restore the testdb database:


psql testdb < testdb_backup.sql
Example Question:
Describe the steps to backup and restore a specific table in PostgreSQL.

User Management
Example:
Create a new user role:


CREATE ROLE new_user WITH LOGIN PASSWORD 'password';
Example Question:
Explain how you would grant a user read-only access to a specific table in PostgreSQL.

Joining Tables
Example:
Perform an INNER JOIN between employees and departments tables:


SELECT employees.name, departments.name 
FROM employees 
INNER JOIN departments ON employees.department_id = departments.id;
Example Question:
How do you write a query to fetch records common to two tables based on a related column?