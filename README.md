# SQL: The Complete A-to-Z Guide

> **Learn SQL from beginner to advanced level using easy English, clear explanations, and practical examples.**
>
> This guide is designed for students, beginners, developers, and anyone who wants to work with databases. Read it from top to bottom, practise every query, and use the final project to test your skills.

---

## Table of Contents

1. [What Is SQL?](#1-what-is-sql)
2. [Database, DBMS, RDBMS, and Tables](#2-database-dbms-rdbms-and-tables)
3. [How SQL Works](#3-how-sql-works)
4. [SQL vs MySQL vs PostgreSQL vs SQLite](#4-sql-vs-mysql-vs-postgresql-vs-sqlite)
5. [Install a Database and Start Practising](#5-install-a-database-and-start-practising)
6. [Your First SQL Query](#6-your-first-sql-query)
7. [SQL Data Types](#7-sql-data-types)
8. [Create a Database and Tables](#8-create-a-database-and-tables)
9. [Keys and Constraints](#9-keys-and-constraints)
10. [Insert Data: INSERT](#10-insert-data-insert)
11. [Read Data: SELECT](#11-read-data-select)
12. [Filter Data: WHERE](#12-filter-data-where)
13. [Sort and Limit Results](#13-sort-and-limit-results)
14. [Aliases and DISTINCT](#14-aliases-and-distinct)
15. [SQL Operators](#15-sql-operators)
16. [NULL Values](#16-null-values)
17. [Built-in SQL Functions](#17-built-in-sql-functions)
18. [Aggregate Functions](#18-aggregate-functions)
19. [GROUP BY and HAVING](#19-group-by-and-having)
20. [Joins](#20-joins)
21. [Subqueries](#21-subqueries)
22. [Set Operators](#22-set-operators)
23. [Conditional Logic: CASE](#23-conditional-logic-case)
24. [Change Data: UPDATE and DELETE](#24-change-data-update-and-delete)
25. [Change Table Structure: ALTER, DROP, and TRUNCATE](#25-change-table-structure-alter-drop-and-truncate)
26. [Relationships and Database Design](#26-relationships-and-database-design)
27. [Database Normalization](#27-database-normalization)
28. [Views](#28-views)
29. [Indexes and Query Performance](#29-indexes-and-query-performance)
30. [Transactions and ACID](#30-transactions-and-acid)
31. [Common Table Expressions (CTEs)](#31-common-table-expressions-ctes)
32. [Window Functions](#32-window-functions)
33. [Advanced SQL Objects](#33-advanced-sql-objects)
34. [Security and SQL Injection](#34-security-and-sql-injection)
35. [Backup, Restore, and Data Import/Export](#35-backup-restore-and-data-importexport)
36. [SQL with Application Code](#36-sql-with-application-code)
37. [A Practical Company Database Project](#37-a-practical-company-database-project)
38. [Practice Questions with Answers](#38-practice-questions-with-answers)
39. [Common SQL Interview Questions](#39-common-sql-interview-questions)
40. [Common Beginner Mistakes](#40-common-beginner-mistakes)
41. [SQL Best Practices](#41-sql-best-practices)
42. [SQL Command Cheat Sheet](#42-sql-command-cheat-sheet)
43. [SQL Learning Roadmap](#43-sql-learning-roadmap)
44. [Glossary](#44-glossary)

---

# 1. What Is SQL?

**SQL** means **Structured Query Language**. It is a language used to communicate with a relational database.

With SQL, you can:

- Create databases and tables.
- Save new data.
- Read and search for data.
- Update existing data.
- Delete data.
- Connect related tables.
- Group and analyse information.
- Control access to data.
- Protect changes with transactions.

For example, imagine that you run an online shop. Your database may store customers, products, orders, and payments. SQL lets you ask questions such as:

- Which products cost more than $50?
- How many orders did each customer make?
- What is the total sales amount this month?
- Which products have never been ordered?

SQL is **declarative**: you describe the result you want, and the database system decides how to find it.

## Why should you learn SQL?

SQL is useful in backend development, web development, data analysis, business intelligence, finance, reporting, testing, and many other areas. Even when an application is written in JavaScript, Python, Java, PHP, or another language, it may use SQL to store and retrieve data.

---

# 2. Database, DBMS, RDBMS, and Tables

## What is data?

Data is recorded information. Examples include a person's name, age, email address, product price, and order date.

## What is a database?

A **database** is an organised collection of data that can be stored, searched, changed, and managed.

## What is a DBMS?

A **Database Management System (DBMS)** is software that helps users and applications create, manage, secure, and query databases.

Examples include PostgreSQL, MySQL, SQLite, Microsoft SQL Server, and Oracle Database.

## What is an RDBMS?

A **Relational Database Management System (RDBMS)** stores data in tables and connects related tables through keys.

A relational table looks similar to a spreadsheet:

| employee_id | name | department | salary |
|---:|---|---|---:|
| 1 | Ayesha | Engineering | 65000 |
| 2 | Rahim | Marketing | 52000 |
| 3 | Nila | Engineering | 70000 |

Important terms:

- **Table:** A collection of related records, such as `employees`.
- **Row / Record:** One individual entry in a table.
- **Column / Field:** One type of information, such as `name` or `salary`.
- **Cell:** One value at the intersection of a row and a column.
- **Schema:** The structure of a database, including tables, columns, relationships, and other objects.
- **Query:** A request or command sent to a database.

---

# 3. How SQL Works

A typical application works like this:

1. A user performs an action, such as signing in or placing an order.
2. The application sends a SQL query to the database.
3. The database checks the query and the user's permissions.
4. The database reads or changes the required data.
5. The database returns a result or an error.
6. The application displays or uses the result.

Example:

```sql
SELECT name, email
FROM customers
WHERE customer_id = 1;
```

This asks the database to return the name and email of the customer whose ID is `1`.

SQL is not the database itself. SQL is the language; PostgreSQL, MySQL, and other database systems are software that understand SQL and manage the data.

---

# 4. SQL vs MySQL vs PostgreSQL vs SQLite

These names are related, but they do not mean the same thing.

| Name | What it is | Common use |
|---|---|---|
| SQL | A database query language | Communicating with relational databases |
| MySQL | A relational database system | Websites and web applications |
| PostgreSQL | A relational database system | Applications needing powerful SQL features and data integrity |
| SQLite | A small, file-based relational database | Learning, prototypes, mobile apps, and embedded applications |
| SQL Server | Microsoft's relational database system | Business and enterprise applications |
| Oracle Database | An enterprise relational database system | Large enterprise systems |

The main SQL ideas are shared, but some syntax and features differ between systems. This is called a **SQL dialect**.

For this guide, examples use broadly familiar SQL and mainly PostgreSQL-style syntax. Check your database system's documentation when syntax differs.

Examples of differences:

- Limiting rows: PostgreSQL/MySQL/SQLite commonly use `LIMIT`; SQL Server commonly uses `TOP` or `OFFSET ... FETCH`.
- Automatically generated IDs: MySQL uses `AUTO_INCREMENT`; PostgreSQL supports identity columns; SQL Server uses `IDENTITY`; SQLite commonly uses `INTEGER PRIMARY KEY`.
- String concatenation and date functions can also differ.
- Not every system supports every join or advanced feature in exactly the same way.

---

# 5. Install a Database and Start Practising

You need a database system and a tool for sending SQL queries.

## Beginner-friendly choices

**Option A: SQLite**

SQLite is a good choice for a quick start. It stores a database in a file and usually does not require a separate database server. You can use the SQLite command-line tool or a graphical tool such as DB Browser for SQLite.

**Option B: PostgreSQL**

PostgreSQL is an excellent choice for learning professional relational database concepts. Install PostgreSQL and optionally use pgAdmin or another SQL editor.

**Option C: MySQL**

MySQL is widely used in web development. You can install MySQL Server and use MySQL Workbench or another SQL client.

## Your first practice plan

1. Install one database system.
2. Open its SQL editor or command-line client.
3. Create a practice database if your system uses named databases.
4. Run the example queries in this guide.
5. Change the values and predict the result before running each query.

Do not try to learn every database product at once. Learn the SQL concepts first, then learn the specific dialect used by your project.

---

# 6. Your First SQL Query

A SQL statement is usually ended with a semicolon (`;`). SQL keywords are commonly written in uppercase to make queries easier to read, but many database systems do not require uppercase keywords.

```sql
SELECT 'Hello, SQL!' AS message;
```

Result:

| message |
|---|
| Hello, SQL! |

A simple query can also calculate a value:

```sql
SELECT 10 + 20 AS total;
```

Result: `30`.

## SQL comments

Use comments to explain your SQL code.

```sql
-- This is a single-line comment.

/*
   This is a multi-line comment.
   It can explain a longer query.
*/

SELECT 1;
```

---

# 7. SQL Data Types

A data type defines what kind of value a column can store.

| Data type | Purpose | Example |
|---|---|---|
| `INT` / `INTEGER` | Whole numbers | `25` |
| `SMALLINT` | Smaller whole numbers | `100` |
| `BIGINT` | Large whole numbers | `9000000000` |
| `DECIMAL(p, s)` / `NUMERIC(p, s)` | Exact decimal values | `1250.75` |
| `REAL` / `FLOAT` / `DOUBLE` | Approximate decimal values | `3.14159` |
| `CHAR(n)` | Fixed-length text | `'BD'` |
| `VARCHAR(n)` | Variable-length text with a limit | `'Ayesha'` |
| `TEXT` | Longer text | `'A product description'` |
| `BOOLEAN` | True or false | `TRUE` |
| `DATE` | Calendar date | `DATE '2026-11-16'` |
| `TIME` | Time of day | `TIME '14:30:00'` |
| `TIMESTAMP` | Date and time | `TIMESTAMP '2026-11-16 14:30:00'` |
| `TIMESTAMP WITH TIME ZONE` | Date and time with time-zone awareness | System-specific representation |
| `BLOB` / `BYTEA` | Binary data | An image or file's bytes |
| `JSON` / `JSONB` | JSON data | `{"active": true}` |

### Choosing data types

- Use integer types for counts and identifiers when appropriate.
- Use `DECIMAL` or `NUMERIC` for money and values that need exact decimal arithmetic. Floating-point types are approximate.
- Choose a text length that matches your requirements, but do not make assumptions about a person's name or address having a tiny maximum length.
- Use date/time types for dates and times instead of storing them as ordinary text.
- Use a boolean type for true/false values when supported.
- Store passwords as secure password hashes in application authentication systems, not as plain text.

Exact available types vary by database system.

---

# 8. Create a Database and Tables

## CREATE DATABASE

In database systems that support it:

```sql
CREATE DATABASE company_db;
```

Then connect to `company_db` using your database client. The way you connect or switch databases depends on the tool and database system.

## CREATE TABLE

A table is created with `CREATE TABLE`.

```sql
CREATE TABLE students (
    student_id INT PRIMARY KEY,
    full_name VARCHAR(100) NOT NULL,
    age INT,
    email VARCHAR(150) UNIQUE
);
```

This table contains four columns:

- `student_id`: a unique student identifier.
- `full_name`: text that must be supplied.
- `age`: a whole number; it may be missing unless another constraint is added.
- `email`: a unique email value; it may be missing unless `NOT NULL` is also added.

## IF NOT EXISTS

Some database systems support this form:

```sql
CREATE TABLE IF NOT EXISTS notes (
    note_id INT PRIMARY KEY,
    note_text TEXT
);
```

It avoids an error when the table already exists, but exact support and behaviour can vary.

---

# 9. Keys and Constraints

Constraints are rules that protect the quality and consistency of data.

## PRIMARY KEY

A primary key uniquely identifies each row. It cannot be `NULL`, and a table has one primary key constraint (which may contain multiple columns).

```sql
CREATE TABLE users (
    user_id INT PRIMARY KEY,
    username VARCHAR(50) NOT NULL
);
```

## FOREIGN KEY

A foreign key connects a column or group of columns to a key in another table. It helps prevent references to records that do not exist.

```sql
CREATE TABLE departments (
    department_id INT PRIMARY KEY,
    department_name VARCHAR(100) NOT NULL
);

CREATE TABLE employees (
    employee_id INT PRIMARY KEY,
    employee_name VARCHAR(100) NOT NULL,
    department_id INT,
    FOREIGN KEY (department_id)
        REFERENCES departments(department_id)
);
```

## UNIQUE

A `UNIQUE` constraint prevents duplicate values in the constrained column or column combination.

```sql
CREATE TABLE accounts (
    account_id INT PRIMARY KEY,
    email VARCHAR(150) UNIQUE
);
```

The way a database handles multiple `NULL` values in a unique column can differ.

## NOT NULL

Requires a value to be supplied.

```sql
name VARCHAR(100) NOT NULL
```

## CHECK

Checks that a value follows a condition.

```sql
CREATE TABLE products (
    product_id INT PRIMARY KEY,
    product_name VARCHAR(100) NOT NULL,
    price DECIMAL(10, 2) NOT NULL CHECK (price >= 0)
);
```

## DEFAULT

Provides a value when an insert does not supply one.

```sql
CREATE TABLE tasks (
    task_id INT PRIMARY KEY,
    status VARCHAR(20) DEFAULT 'pending'
);
```

A default is used when the column is omitted from the insert (or `DEFAULT` is requested). It does not generally replace an explicitly supplied `NULL`.

## Composite key

A composite key contains more than one column.

```sql
CREATE TABLE course_enrolments (
    student_id INT,
    course_id INT,
    enrolled_on DATE,
    PRIMARY KEY (student_id, course_id)
);
```

The pair `(student_id, course_id)` must be unique.

---

# 10. Insert Data: INSERT

`INSERT` adds new rows to a table.

## Insert one row

```sql
INSERT INTO students (student_id, full_name, age, email)
VALUES (1, 'Ayesha Rahman', 21, 'ayesha@example.com');
```

## Insert multiple rows

```sql
INSERT INTO students (student_id, full_name, age, email)
VALUES
    (2, 'Rahim Ahmed', 22, 'rahim@example.com'),
    (3, 'Nila Islam', 20, 'nila@example.com');
```

## Insert only selected columns

```sql
INSERT INTO students (student_id, full_name)
VALUES (4, 'Tanvir Hasan');
```

The other columns receive their default values or `NULL` if allowed.

## Insert rows from another query

```sql
INSERT INTO archived_students (student_id, full_name)
SELECT student_id, full_name
FROM students
WHERE age >= 25;
```

The target table must have compatible columns.

## Generated IDs

Most database systems provide a way to generate IDs automatically, but the syntax differs. For example:

```sql
-- PostgreSQL identity-column example
CREATE TABLE generated_users (
    user_id INT GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
    username VARCHAR(80) NOT NULL
);

INSERT INTO generated_users (username)
VALUES ('samira');
```

For MySQL, look up `AUTO_INCREMENT`; for SQL Server, look up `IDENTITY`; for SQLite, look up `INTEGER PRIMARY KEY` behaviour. Do not assume one system's identity syntax works unchanged in another.

---

# 11. Read Data: SELECT

`SELECT` reads data from one or more tables.

## Select all columns

```sql
SELECT *
FROM students;
```

`*` means all columns. It is useful when exploring a table, but production queries are usually clearer and more stable when they name the columns they need.

## Select particular columns

```sql
SELECT full_name, email
FROM students;
```

## Select an expression

```sql
SELECT full_name, age, age + 1 AS age_next_year
FROM students;
```

## Logical order of a SELECT query

A useful simplified logical order is:

1. `FROM` and `JOIN` identify the source rows.
2. `WHERE` filters rows.
3. `GROUP BY` forms groups.
4. `HAVING` filters groups.
5. `SELECT` calculates output expressions.
6. `DISTINCT` removes duplicate output rows.
7. `ORDER BY` sorts the output.
8. `LIMIT` / `OFFSET` or the system's equivalent restricts the returned rows.

This is a logical explanation, not necessarily the physical execution order chosen by the database engine.

---

# 12. Filter Data: WHERE

`WHERE` returns only rows that match a condition.

```sql
SELECT *
FROM students
WHERE age >= 21;
```

## Comparison operators

| Operator | Meaning |
|---|---|
| `=` | Equal to |
| `<>` | Not equal to (standard SQL) |
| `!=` | Not equal to (supported by many systems) |
| `>` | Greater than |
| `<` | Less than |
| `>=` | Greater than or equal to |
| `<=` | Less than or equal to |

Example:

```sql
SELECT *
FROM products
WHERE price < 100;
```

## AND

All conditions must be true.

```sql
SELECT *
FROM students
WHERE age >= 18 AND age <= 25;
```

## OR

At least one condition must be true.

```sql
SELECT *
FROM students
WHERE age < 18 OR age > 60;
```

## NOT

Reverses a condition.

```sql
SELECT *
FROM students
WHERE NOT age = 20;
```

For mixed `AND` and `OR` conditions, use parentheses so the meaning is clear.

```sql
SELECT *
FROM employees
WHERE department_id = 2
  AND (salary > 50000 OR job_title = 'Manager');
```

## BETWEEN

Checks whether a value is within an inclusive range.

```sql
SELECT *
FROM products
WHERE price BETWEEN 20 AND 100;
```

This includes `20` and `100`.

## IN

Checks whether a value matches one of several values.

```sql
SELECT *
FROM employees
WHERE department_id IN (1, 3, 5);
```

## LIKE

Searches text using patterns.

- `%` matches zero or more characters.
- `_` matches exactly one character.

```sql
-- Names beginning with A
SELECT * FROM students
WHERE full_name LIKE 'A%';

-- Names ending with n
SELECT * FROM students
WHERE full_name LIKE '%n';

-- Names containing "rah"
SELECT * FROM students
WHERE full_name LIKE '%rah%';

-- Exactly four characters, beginning with A
SELECT * FROM students
WHERE full_name LIKE 'A___';
```

Whether `LIKE` is case-sensitive depends on the database and its collation settings. PostgreSQL also supports `ILIKE` for case-insensitive pattern matching.

## EXISTS

`EXISTS` checks whether a subquery returns at least one row.

```sql
SELECT c.customer_id, c.customer_name
FROM customers AS c
WHERE EXISTS (
    SELECT 1
    FROM orders AS o
    WHERE o.customer_id = c.customer_id
);
```

This returns customers who have at least one order.

---

# 13. Sort and Limit Results

## ORDER BY

Sorts query results.

```sql
SELECT *
FROM products
ORDER BY price ASC;
```

- `ASC`: ascending order (usually the default).
- `DESC`: descending order.

Sort by multiple columns:

```sql
SELECT *
FROM employees
ORDER BY department_id ASC, salary DESC;
```

This sorts by department first, then by salary inside each department.

## LIMIT and OFFSET

Common in PostgreSQL, MySQL, and SQLite:

```sql
-- Return the five most expensive products
SELECT *
FROM products
ORDER BY price DESC
LIMIT 5;

-- Skip the first five rows and return the next five
SELECT *
FROM products
ORDER BY product_id
LIMIT 5 OFFSET 5;
```

Always use an appropriate `ORDER BY` when you need predictable pagination. Without ordering, which rows appear first is not guaranteed.

SQL Server commonly uses `TOP` or `OFFSET ... FETCH`; other systems may use different syntax.

---

# 14. Aliases and DISTINCT

## Column alias

An alias gives an output column a temporary name.

```sql
SELECT product_name AS name,
       price AS unit_price
FROM products;
```

## Table alias

```sql
SELECT e.employee_name, d.department_name
FROM employees AS e
JOIN departments AS d
    ON e.department_id = d.department_id;
```

Aliases make long queries shorter and easier to read.

## DISTINCT

Removes duplicate combinations from the output.

```sql
SELECT DISTINCT department_id
FROM employees;
```

For multiple columns, it returns unique combinations of those columns:

```sql
SELECT DISTINCT city, country
FROM customers;
```

`DISTINCT` does not change the data stored in the table.

---

# 15. SQL Operators

SQL uses several kinds of operators.

## Arithmetic operators

| Operator | Meaning | Example |
|---|---|---|
| `+` | Addition | `price + 5` |
| `-` | Subtraction | `price - 5` |
| `*` | Multiplication | `price * 2` |
| `/` | Division | `price / 2` |
| `%` | Remainder in systems that support it | `number % 2` |

```sql
SELECT product_name,
       price,
       price * 0.10 AS discount_amount,
       price * 0.90 AS discounted_price
FROM products;
```

## Comparison operators

Comparison operators compare two values and produce a true/false/unknown result depending on the values and `NULL` rules.

## Logical operators

`AND`, `OR`, and `NOT` combine or reverse conditions.

## Concatenation

Concatenation joins text values. Syntax varies by database system.

```sql
-- PostgreSQL and SQLite use || for string concatenation
SELECT first_name || ' ' || last_name AS full_name
FROM people;
```

Some systems use `CONCAT()` or another operator. Check your database's syntax.

---

# 16. NULL Values

`NULL` means a value is missing, unknown, or not supplied. It is not the same as `0`, an empty string (`''`), or the word `'NULL'`.

## Find NULL values

Use `IS NULL`:

```sql
SELECT *
FROM students
WHERE email IS NULL;
```

Use `IS NOT NULL`:

```sql
SELECT *
FROM students
WHERE email IS NOT NULL;
```

Do not write `email = NULL`. Comparisons with `NULL` use SQL's unknown logic, so `= NULL` does not work as a NULL test.

## COALESCE

Returns the first value that is not `NULL`.

```sql
SELECT student_id,
       COALESCE(email, 'No email provided') AS email_display
FROM students;
```

## NULLIF

Returns `NULL` when two expressions are equal; otherwise, it returns the first expression.

```sql
SELECT total_sales / NULLIF(order_count, 0) AS average_order_value
FROM sales_summary;
```

This can help avoid division by zero, although the exact result type still depends on the database.

## Important NULL rules

- `NULL = NULL` is not true; it is unknown.
- `COUNT(column)` ignores `NULL` values.
- `COUNT(*)` counts rows, including rows whose columns contain `NULL`.
- Use `IS NULL` and `IS NOT NULL` to test for missing values.

---

# 17. Built-in SQL Functions

Functions take values as input and return a result. Available functions and names can vary by database.

## String functions

```sql
SELECT UPPER('hello');          -- HELLO
SELECT LOWER('HELLO');          -- hello
SELECT LENGTH('Database');      -- character/byte behaviour can vary
SELECT TRIM('  SQL  ');         -- SQL
SELECT SUBSTRING('Database' FROM 1 FOR 4); -- Data (syntax varies)
```

Other common string functions include `REPLACE`, `CONCAT`, and `POSITION`.

Example with a table:

```sql
SELECT UPPER(full_name) AS uppercase_name
FROM students;
```

## Numeric functions

```sql
SELECT ROUND(12.567, 2);  -- commonly 12.57
SELECT ABS(-25);          -- 25
SELECT CEILING(4.2);      -- commonly 5
SELECT FLOOR(4.8);        -- commonly 4
```

Names such as `CEILING` and `CEIL`, as well as rounding details, can vary.

## Date and time functions

```sql
SELECT CURRENT_DATE;
SELECT CURRENT_TIME;
SELECT CURRENT_TIMESTAMP;
```

Date arithmetic, extracting a year or month, and formatting a date have different syntax across database systems. Use the official documentation for your database.

## Type conversion

`CAST` converts a value to another type when the conversion is valid.

```sql
SELECT CAST('123' AS INTEGER) AS number_value;
```

Some systems also support a shorter conversion operator or additional conversion functions.

---

# 18. Aggregate Functions

Aggregate functions calculate one result from multiple rows.

| Function | Purpose |
|---|---|
| `COUNT()` | Counts rows or non-NULL values |
| `SUM()` | Adds numeric values |
| `AVG()` | Calculates the average of non-NULL numeric values |
| `MIN()` | Finds the smallest value |
| `MAX()` | Finds the largest value |

Examples:

```sql
SELECT COUNT(*) AS total_students
FROM students;

SELECT AVG(age) AS average_age
FROM students;

SELECT MIN(price) AS lowest_price,
       MAX(price) AS highest_price,
       SUM(price) AS sum_of_prices
FROM products;
```

Important difference:

```sql
SELECT COUNT(*) FROM students;      -- counts every row
SELECT COUNT(email) FROM students;  -- counts rows with a non-NULL email
```

`SUM()` and `AVG()` ignore `NULL` values. If there are no non-NULL values, aggregate results such as `SUM` and `AVG` can be `NULL` rather than zero.

---

# 19. GROUP BY and HAVING

## GROUP BY

`GROUP BY` collects rows that share the same value so you can calculate one result per group.

```sql
SELECT department_id,
       COUNT(*) AS employee_count
FROM employees
GROUP BY department_id;
```

Example: total orders per customer.

```sql
SELECT customer_id,
       COUNT(*) AS total_orders
FROM orders
GROUP BY customer_id;
```

## HAVING

`HAVING` filters groups after grouping. `WHERE` filters individual rows before grouping.

```sql
SELECT customer_id,
       COUNT(*) AS total_orders
FROM orders
GROUP BY customer_id
HAVING COUNT(*) >= 3;
```

## WHERE vs HAVING

| WHERE | HAVING |
|---|---|
| Filters rows before grouping | Filters groups after grouping |
| Commonly used with ordinary column conditions | Commonly used with aggregate conditions |
| Appears before `GROUP BY` | Appears after `GROUP BY` |

Example using both:

```sql
SELECT department_id,
       AVG(salary) AS average_salary
FROM employees
WHERE salary > 20000
GROUP BY department_id
HAVING AVG(salary) > 40000;
```

---

# 20. Joins

A join combines related rows from two or more tables. Joins are one of the most important SQL skills.

Assume these tables:

**customers**

| customer_id | customer_name |
|---:|---|
| 1 | Ayesha |
| 2 | Rahim |
| 3 | Nila |

**orders**

| order_id | customer_id | total_amount |
|---:|---:|---:|
| 101 | 1 | 500 |
| 102 | 1 | 250 |
| 103 | 2 | 900 |

## INNER JOIN

Returns only rows that match in both tables.

```sql
SELECT c.customer_name,
       o.order_id,
       o.total_amount
FROM customers AS c
INNER JOIN orders AS o
    ON c.customer_id = o.customer_id;
```

Nila does not appear because Nila has no matching order.

## LEFT JOIN (LEFT OUTER JOIN)

Returns every row from the left table and matching rows from the right table. If there is no match, right-side columns contain `NULL`.

```sql
SELECT c.customer_name,
       o.order_id
FROM customers AS c
LEFT JOIN orders AS o
    ON c.customer_id = o.customer_id;
```

Nila appears with a `NULL` order ID.

Find customers with no orders:

```sql
SELECT c.customer_id, c.customer_name
FROM customers AS c
LEFT JOIN orders AS o
    ON c.customer_id = o.customer_id
WHERE o.order_id IS NULL;
```

## RIGHT JOIN (RIGHT OUTER JOIN)

Returns every row from the right table and matching rows from the left table.

```sql
SELECT c.customer_name,
       o.order_id
FROM customers AS c
RIGHT JOIN orders AS o
    ON c.customer_id = o.customer_id;
```

You can often rewrite a right join as a left join by reversing the table order.

## FULL OUTER JOIN

Returns matching rows plus unmatched rows from both sides. Missing-side columns are `NULL`.

```sql
SELECT c.customer_name,
       o.order_id
FROM customers AS c
FULL OUTER JOIN orders AS o
    ON c.customer_id = o.customer_id;
```

Not every database system supports `FULL OUTER JOIN` directly. MySQL, for example, commonly requires a `LEFT JOIN` / `RIGHT JOIN` plus a `UNION` approach.

## CROSS JOIN

Returns every possible combination of rows from both tables.

```sql
SELECT c.customer_name,
       p.product_name
FROM customers AS c
CROSS JOIN products AS p;
```

If one table has 3 rows and the other has 4 rows, the result has 12 combinations.

## SELF JOIN

A table can be joined to itself. This is useful for relationships such as employees and their managers.

```sql
SELECT e.employee_name AS employee,
       m.employee_name AS manager
FROM employees AS e
LEFT JOIN employees AS m
    ON e.manager_id = m.employee_id;
```

## Join with more than two tables

```sql
SELECT o.order_id,
       c.customer_name,
       p.product_name,
       oi.quantity
FROM orders AS o
JOIN customers AS c
    ON o.customer_id = c.customer_id
JOIN order_items AS oi
    ON o.order_id = oi.order_id
JOIN products AS p
    ON oi.product_id = p.product_id;
```

## Important join tips

- Always understand which table should provide all rows.
- Use clear aliases such as `c` for customers and `o` for orders.
- Make the join condition explicit with `ON`.
- Be careful when joining two one-to-many relationships because rows can multiply.
- A condition on the right table in `WHERE` can remove unmatched rows from a `LEFT JOIN`. When you need to preserve unmatched rows, check whether that condition belongs in the `ON` clause instead.

---

# 21. Subqueries

A **subquery** is a query placed inside another SQL statement.

## Subquery in WHERE

Find products that cost more than the average price:

```sql
SELECT product_name, price
FROM products
WHERE price > (
    SELECT AVG(price)
    FROM products
);
```

## Subquery with IN

```sql
SELECT customer_name
FROM customers
WHERE customer_id IN (
    SELECT customer_id
    FROM orders
);
```

This returns customers whose IDs appear in the orders table.

## Subquery in FROM

```sql
SELECT department_summary.department_id,
       department_summary.average_salary
FROM (
    SELECT department_id, AVG(salary) AS average_salary
    FROM employees
    GROUP BY department_id
) AS department_summary;
```

A subquery in `FROM` is often called a **derived table**. Most systems require it to have an alias.

## Correlated subquery

A correlated subquery refers to a value from the outer query.

```sql
SELECT e.employee_name, e.salary, e.department_id
FROM employees AS e
WHERE e.salary > (
    SELECT AVG(e2.salary)
    FROM employees AS e2
    WHERE e2.department_id = e.department_id
);
```

This finds employees whose salary is higher than the average salary in their own department.

## EXISTS vs IN

Both can be useful. `EXISTS` checks for a matching row, while `IN` compares a value against a set of values. For `NOT IN`, be careful: a `NULL` inside the subquery result can produce surprising results. `NOT EXISTS` is often a safer choice for anti-join logic.

---

# 22. Set Operators

Set operators combine the results of multiple `SELECT` queries. The queries must return the same number of columns, in compatible types and corresponding positions.

## UNION

Combines results and removes duplicates.

```sql
SELECT city FROM customers
UNION
SELECT city FROM suppliers;
```

## UNION ALL

Combines results and keeps duplicates. It is usually faster than `UNION` when duplicate removal is unnecessary.

```sql
SELECT city FROM customers
UNION ALL
SELECT city FROM suppliers;
```

## INTERSECT

Returns rows that appear in both results. Support varies by database version/system.

```sql
SELECT city FROM customers
INTERSECT
SELECT city FROM suppliers;
```

## EXCEPT

Returns rows from the first result that do not appear in the second. Some systems use the name `MINUS` instead.

```sql
SELECT city FROM customers
EXCEPT
SELECT city FROM suppliers;
```

An `ORDER BY` for a combined result is normally written at the end of the complete set expression.

---

# 23. Conditional Logic: CASE

`CASE` adds if/else-style logic to a query.

```sql
SELECT employee_name,
       salary,
       CASE
           WHEN salary >= 70000 THEN 'High'
           WHEN salary >= 40000 THEN 'Medium'
           ELSE 'Entry'
       END AS salary_level
FROM employees;
```

A `CASE` expression returns the result of the first matching `WHEN` branch. You can use it in `SELECT`, `ORDER BY`, and other expressions.

Example: calculate a discount category.

```sql
SELECT product_name,
       price,
       CASE
           WHEN price >= 1000 THEN 'Premium'
           WHEN price >= 100 THEN 'Standard'
           ELSE 'Budget'
       END AS price_category
FROM products;
```

---

# 24. Change Data: UPDATE and DELETE

## UPDATE

`UPDATE` changes existing rows.

```sql
UPDATE students
SET age = 22
WHERE student_id = 1;
```

Update more than one column:

```sql
UPDATE students
SET age = 23,
    email = 'new-email@example.com'
WHERE student_id = 1;
```

Update using an expression:

```sql
UPDATE products
SET price = price * 1.10
WHERE category = 'Accessories';
```

**Warning:** An `UPDATE` without a `WHERE` condition can update every row in the table.

## DELETE

`DELETE` removes rows.

```sql
DELETE FROM students
WHERE student_id = 4;
```

**Warning:** A `DELETE` without a `WHERE` condition can remove every row in the table.

## Safe workflow for UPDATE and DELETE

Before changing data:

1. Write a `SELECT` with the same `WHERE` condition.
2. Check that it returns exactly the rows you intend to change.
3. Use a transaction when appropriate.
4. Run the update or delete.
5. Verify the result before committing when using a transaction.

Example:

```sql
BEGIN;

SELECT *
FROM products
WHERE product_id = 10;

UPDATE products
SET price = 19.99
WHERE product_id = 10;

SELECT *
FROM products
WHERE product_id = 10;

-- Use COMMIT only after verifying the result.
-- Use ROLLBACK if the change is wrong.
ROLLBACK;
```

This example intentionally ends with `ROLLBACK`, so the change is not kept. Transaction syntax and behaviour can vary by system and client.

---

# 25. Change Table Structure: ALTER, DROP, and TRUNCATE

## ALTER TABLE

Changes the structure of an existing table. Exact syntax varies.

Add a column:

```sql
ALTER TABLE students
ADD COLUMN phone VARCHAR(25);
```

Change a column type (PostgreSQL-style example):

```sql
ALTER TABLE students
ALTER COLUMN phone TYPE VARCHAR(30);
```

Rename a column (syntax varies):

```sql
ALTER TABLE students
RENAME COLUMN phone TO phone_number;
```

Add a constraint:

```sql
ALTER TABLE students
ADD CONSTRAINT students_age_check CHECK (age >= 0);
```

Drop a column (check dependencies first):

```sql
ALTER TABLE students
DROP COLUMN phone_number;
```

## DROP TABLE

Deletes a table definition and its data.

```sql
DROP TABLE students;
```

Some systems support:

```sql
DROP TABLE IF EXISTS students;
```

## TRUNCATE TABLE

Removes all rows from a table while keeping the table structure.

```sql
TRUNCATE TABLE temporary_logs;
```

`TRUNCATE` behaviour differs across database systems, especially for transactions, identity counters, foreign keys, and triggers. Do not assume it works exactly like `DELETE`.

## DELETE vs TRUNCATE vs DROP

| Command | What it does |
|---|---|
| `DELETE` | Removes selected rows, or all rows if no filter is used |
| `TRUNCATE` | Quickly removes all rows while keeping the table structure (system-specific behaviour) |
| `DROP` | Removes the table object itself, including its structure |

These operations can cause serious data loss. Confirm the target and take backups before using them on important data.

---

# 26. Relationships and Database Design

Relational databases connect tables through keys.

## One-to-one relationship

One row in Table A is related to at most one row in Table B, and vice versa.

Example: one user has one profile. A unique foreign key can help enforce this relationship.

## One-to-many relationship

One row in Table A can be related to many rows in Table B.

Example: one customer can place many orders. The `orders` table stores `customer_id` as a foreign key.

## Many-to-many relationship

Many rows in Table A can relate to many rows in Table B.

Example: students can take many courses, and each course can have many students. Use a junction/bridge table:

```sql
CREATE TABLE students (
    student_id INT PRIMARY KEY,
    student_name VARCHAR(100) NOT NULL
);

CREATE TABLE courses (
    course_id INT PRIMARY KEY,
    course_name VARCHAR(100) NOT NULL
);

CREATE TABLE student_courses (
    student_id INT NOT NULL,
    course_id INT NOT NULL,
    enrolled_on DATE,
    PRIMARY KEY (student_id, course_id),
    FOREIGN KEY (student_id) REFERENCES students(student_id),
    FOREIGN KEY (course_id) REFERENCES courses(course_id)
);
```

The bridge table converts a many-to-many relationship into two one-to-many relationships.

## Referential actions

When a referenced parent row is updated or deleted, a foreign key can define what should happen. Common actions include:

- `ON DELETE RESTRICT` / `NO ACTION`: prevent or reject a delete that would break the relationship (exact timing can vary).
- `ON DELETE CASCADE`: delete related child rows automatically.
- `ON DELETE SET NULL`: set the child foreign key to `NULL`, when allowed.
- `ON UPDATE CASCADE`: update child references when the parent key changes.

Use cascading actions carefully. They can affect many rows.

---

# 27. Database Normalization

**Normalization** is the process of organising relational data to reduce unnecessary duplication and avoid update problems.

Imagine storing this information in one table:

| order_id | customer_name | customer_email | product_1 | product_2 |
|---:|---|---|---|---|
| 1 | Ayesha | a@example.com | Keyboard | Mouse |
| 2 | Ayesha | a@example.com | Monitor | NULL |

This structure repeats customer details and creates problems when an order contains many products.

A more organised design separates customers, orders, products, and order items into related tables.

## First Normal Form (1NF)

Common teaching rules for 1NF:

- Each column stores one value per row (no repeating lists or groups inside a cell).
- Each row can be identified.
- Values in a column follow a consistent type/domain.

## Second Normal Form (2NF)

A table is in 1NF and every non-key column depends on the whole candidate key, not just part of a composite key. This matters when a table has a composite key.

## Third Normal Form (3NF)

A table is in 2NF and non-key columns do not depend transitively on a candidate key through another non-key column.

## Why normalize?

- Reduce duplicate data.
- Make updates safer.
- Prevent insert, update, and delete anomalies.
- Clarify relationships between entities.

## Can too much normalization be a problem?

Highly normalized designs may require more joins. In reporting or high-read systems, carefully measured denormalization may improve performance. Make a correct design first, then optimise based on real workload measurements.

---

# 28. Views

A **view** is a saved query that behaves like a virtual table. In many systems, a normal view stores the query definition rather than a separate copy of its result.

Create a view:

```sql
CREATE VIEW customer_order_totals AS
SELECT c.customer_id,
       c.customer_name,
       COUNT(o.order_id) AS order_count
FROM customers AS c
LEFT JOIN orders AS o
    ON c.customer_id = o.customer_id
GROUP BY c.customer_id, c.customer_name;
```

Read from the view:

```sql
SELECT *
FROM customer_order_totals
WHERE order_count > 2;
```

Drop a view:

```sql
DROP VIEW customer_order_totals;
```

Some databases support **materialized views**, which store query results and must be refreshed. Materialized view support and refresh syntax vary.

Views can simplify complex queries and provide a controlled way to expose selected columns, but permissions must still be configured correctly.

---

# 29. Indexes and Query Performance

An **index** is a data structure that helps the database find rows more quickly for certain queries. Think of it like the index at the back of a book.

Create an index:

```sql
CREATE INDEX idx_customers_email
ON customers(email);
```

A unique index:

```sql
CREATE UNIQUE INDEX idx_users_username
ON users(username);
```

A multi-column (composite) index:

```sql
CREATE INDEX idx_orders_customer_date
ON orders(customer_id, order_date);
```

Drop an index (syntax varies by system):

```sql
DROP INDEX idx_customers_email;
```

## When can an index help?

Indexes may help with columns used frequently in:

- `WHERE` filters.
- Join conditions.
- `ORDER BY` operations.
- Some grouping and range queries.

## Index disadvantages

- Indexes use disk space and memory.
- Inserts, updates, and deletes may become slower because indexes need maintenance.
- Too many indexes make a database harder to maintain.
- A poorly selected index may not be used by the query planner.

## EXPLAIN

`EXPLAIN` shows the database's planned approach to a query.

```sql
EXPLAIN
SELECT *
FROM orders
WHERE customer_id = 10;
```

Some systems support `EXPLAIN ANALYZE` to execute a query and report actual timing and row information. Use it carefully, because it really runs the statement in systems that support that behaviour.

## Practical performance advice

1. Select only the columns you need; avoid unnecessary `SELECT *` in production code.
2. Filter rows as early as your query logic allows.
3. Index columns based on real query patterns, not guesses.
4. Check join conditions and data types.
5. Avoid applying functions to indexed columns in filters when it prevents an efficient index lookup; consider a suitable expression index or a different predicate if needed.
6. Use pagination carefully and prefer stable ordering.
7. Read query plans and measure performance with realistic data.
8. Do not add an index to every column.

---

# 30. Transactions and ACID

A **transaction** is a group of database operations treated as one unit of work.

Example: transferring money from one bank account to another should subtract from one account and add to the other. Both actions must succeed together, or neither should be kept.

## Basic transaction commands

```sql
BEGIN;

UPDATE accounts
SET balance = balance - 100
WHERE account_id = 1;

UPDATE accounts
SET balance = balance + 100
WHERE account_id = 2;

COMMIT;
```

If something goes wrong before committing:

```sql
ROLLBACK;
```

A `COMMIT` makes the transaction's changes permanent according to the database's transaction rules. A `ROLLBACK` cancels uncommitted changes.

## ACID properties

| Property | Meaning |
|---|---|
| Atomicity | All operations in the transaction succeed as a unit, or the transaction is rolled back |
| Consistency | A transaction takes the database from one valid state to another, preserving defined rules |
| Isolation | Concurrent transactions are controlled so their effects follow the database's isolation rules |
| Durability | Committed changes are preserved according to the system's durability guarantees |

## SAVEPOINT

A savepoint lets you roll back part of a transaction in systems that support it.

```sql
BEGIN;

UPDATE products
SET price = price * 1.05;

SAVEPOINT after_price_change;

DELETE FROM products
WHERE product_id = 999;

ROLLBACK TO SAVEPOINT after_price_change;

COMMIT;
```

## Isolation levels

Common SQL isolation-level names include:

- `READ UNCOMMITTED`
- `READ COMMITTED`
- `REPEATABLE READ`
- `SERIALIZABLE`

The exact behaviours, default level, and supported levels vary by database system. Higher isolation can reduce certain concurrency anomalies but may also increase waiting, conflicts, or retries.

---

# 31. Common Table Expressions (CTEs)

A **Common Table Expression (CTE)** is a named query result that exists for one statement. It starts with `WITH` and can make complex queries easier to read.

```sql
WITH high_salary_employees AS (
    SELECT employee_id, employee_name, salary
    FROM employees
    WHERE salary > 50000
)
SELECT *
FROM high_salary_employees
ORDER BY salary DESC;
```

## Multiple CTEs

```sql
WITH order_counts AS (
    SELECT customer_id, COUNT(*) AS total_orders
    FROM orders
    GROUP BY customer_id
),
large_customers AS (
    SELECT customer_id, total_orders
    FROM order_counts
    WHERE total_orders >= 2
)
SELECT c.customer_name, lc.total_orders
FROM large_customers AS lc
JOIN customers AS c
    ON c.customer_id = lc.customer_id;
```

## Recursive CTE

A recursive CTE can work with hierarchical data, such as an organisation chart or category tree. Syntax and limits vary across systems.

PostgreSQL-style example:

```sql
WITH RECURSIVE employee_tree AS (
    -- Start with employees who have no manager
    SELECT employee_id, employee_name, manager_id, 1 AS level
    FROM employees
    WHERE manager_id IS NULL

    UNION ALL

    -- Add employees who report to the previous level
    SELECT e.employee_id, e.employee_name, e.manager_id, et.level + 1
    FROM employees AS e
    JOIN employee_tree AS et
        ON e.manager_id = et.employee_id
)
SELECT *
FROM employee_tree
ORDER BY level, employee_id;
```

Make sure recursive relationships cannot create an endless cycle, or use the database's supported cycle-handling features.

---

# 32. Window Functions

A **window function** calculates a result across a set of related rows without combining those rows into one row per group. Unlike `GROUP BY`, a window function normally keeps each input row in the output.

Window functions use `OVER()`.

## ROW_NUMBER

Assigns a unique sequence number inside a window.

```sql
SELECT employee_name,
       department_id,
       salary,
       ROW_NUMBER() OVER (
           PARTITION BY department_id
           ORDER BY salary DESC
       ) AS row_num
FROM employees;
```

## RANK and DENSE_RANK

```sql
SELECT employee_name,
       salary,
       RANK() OVER (ORDER BY salary DESC) AS salary_rank,
       DENSE_RANK() OVER (ORDER BY salary DESC) AS dense_salary_rank
FROM employees;
```

- `ROW_NUMBER()` gives every row a different number.
- `RANK()` gives tied values the same rank and leaves gaps after ties.
- `DENSE_RANK()` gives tied values the same rank but does not leave gaps.

## PARTITION BY

Creates separate windows, similar to grouping for the window calculation.

```sql
SELECT employee_name,
       department_id,
       salary,
       AVG(salary) OVER (PARTITION BY department_id) AS department_average
FROM employees;
```

Every employee row remains in the result.

## Running total

```sql
SELECT order_id,
       order_date,
       total_amount,
       SUM(total_amount) OVER (
           ORDER BY order_date, order_id
           ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW
       ) AS running_total
FROM orders;
```

## LAG and LEAD

`LAG` reads a value from an earlier row in the window; `LEAD` reads a value from a later row.

```sql
SELECT order_id,
       order_date,
       total_amount,
       LAG(total_amount) OVER (ORDER BY order_date, order_id) AS previous_order_amount,
       LEAD(total_amount) OVER (ORDER BY order_date, order_id) AS next_order_amount
FROM orders;
```

Window functions are especially useful for rankings, running totals, comparisons between periods, and analytics.

---

# 33. Advanced SQL Objects

Advanced database features can be powerful, but their syntax differs greatly between systems.

## Stored procedures

A stored procedure is a named program stored in the database. It can perform one or more operations and may accept parameters. Each database has its own procedure language and syntax.

Typical uses include controlled administrative tasks, repeated database workflows, and operations that are intentionally kept inside the database.

## User-defined functions

A user-defined function is a reusable routine that returns a value or table, depending on the database system. Functions often appear inside SQL expressions.

## Triggers

A trigger runs automatically when a configured event happens, such as an insert, update, or delete.

Possible uses:

- Recording audit information.
- Enforcing specialised rules.
- Maintaining derived data in carefully designed systems.

Triggers can also make application behaviour harder to understand because changes happen automatically. Use them only when the design has a clear reason and is well documented.

## Temporary tables

Temporary tables store short-lived data for a session or transaction, depending on the database.

```sql
CREATE TEMPORARY TABLE recent_orders AS
SELECT *
FROM orders
WHERE order_date >= CURRENT_DATE - INTERVAL '30 days';
```

This interval syntax is PostgreSQL-style and is not portable to every system.

## Sequences

A sequence is a database object that generates numeric values. Some databases use sequences directly; other systems provide identity or auto-increment columns. Do not assume sequence syntax is identical across products.

## JSON data

Some relational database systems support JSON columns and functions. JSON columns can be useful when data is naturally flexible, but frequently queried and strongly structured fields may be better represented as ordinary relational columns. PostgreSQL provides `JSON` and `JSONB`; other systems have their own JSON features.

---

# 34. Security and SQL Injection

Database security is essential. A correct query is not enough if untrusted users can access data they should not see or change.

## SQL injection

SQL injection happens when untrusted input is combined with SQL text in an unsafe way. An attacker may change the meaning of the query.

**Unsafe application pattern (do not use):**

```javascript
// UNSAFE: user input is inserted directly into SQL text.
const sql = "SELECT * FROM users WHERE email = '" + email + "'";
```

## Use parameterized queries

A parameterized query keeps SQL code separate from user-supplied values.

PostgreSQL-style Node.js example using the `pg` package:

```javascript
const result = await pool.query(
  'SELECT user_id, email FROM users WHERE email = $1',
  [email]
);
```

Other drivers use different placeholder formats, such as `?`. Follow the documentation for your database library. Do not build SQL values by joining strings.

For dynamic table names, column names, or sort directions, ordinary value parameters may not work. Use a strict allowlist of permitted identifiers and options.

## Least privilege

Give each database account only the permissions it needs.

Example (syntax and role capabilities vary):

```sql
-- Example role creation and permission grant; adjust for your database.
CREATE ROLE app_reader;
GRANT SELECT ON customers TO app_reader;
```

Avoid using an administrator account for normal application requests.

## More security practices

- Never store passwords in plain text. Use a well-reviewed password hashing method in the application.
- Keep database credentials out of source code and public repositories.
- Use environment variables or a proper secret manager for credentials.
- Encrypt network connections where appropriate.
- Limit network access to the database server.
- Keep database software and drivers updated.
- Give application accounts only necessary permissions.
- Back up important data and test restore procedures.
- Do not expose sensitive columns through public APIs or unrestricted views.
- Log security-relevant events without writing secrets or passwords into logs.

---

# 35. Backup, Restore, and Data Import/Export

A backup is a copy of data that can be used to recover from accidental deletion, hardware failure, or other incidents.

Backup and restore tools are database-specific. Examples include `pg_dump` and `pg_restore` for PostgreSQL, `mysqldump` for MySQL, and SQLite's backup facilities or file-copy procedures performed safely.

Do not assume that copying a live database file is safe for every database system or configuration. Follow the system's official backup method.

## CSV export idea

A CSV file stores tabular data as text. Many database clients provide export tools. Some database systems also support SQL commands for importing or exporting CSV, but permissions and syntax vary.

A simple CSV example:

```text
customer_id,customer_name,city
1,Ayesha,Dhaka
2,Rahim,Chattogram
```

## Import/export checklist

1. Confirm the source and destination.
2. Check the character encoding, delimiter, date format, and decimal format.
3. Check whether the first row contains column names.
4. Validate column types and required fields.
5. Test with a small file first.
6. Check row counts and sample records after import.
7. Protect personal and confidential data during transfer.
8. Keep backups before large changes.

---

# 36. SQL with Application Code

Most real applications use a programming language to connect to a database.

A typical backend flow is:

1. Receive a request from the client.
2. Validate the input.
3. Run a parameterized SQL query.
4. Handle database errors safely.
5. Return only the data the user is allowed to see.

## Example: Node.js with PostgreSQL

Install a PostgreSQL driver in a Node.js project:

```bash
npm install pg
```

Example using ES modules and environment variables:

```javascript
import pg from 'pg';

const { Pool } = pg;

// Store DATABASE_URL in your environment, not directly in source code.
const pool = new Pool({
  connectionString: process.env.DATABASE_URL
});

export async function getCustomerById(customerId) {
  try {
    const result = await pool.query(
      'SELECT customer_id, customer_name, email FROM customers WHERE customer_id = $1',
      [customerId]
    );

    return result.rows[0] ?? null;
  } catch (error) {
    // Log a safe, useful error message in production.
    // Do not send database credentials or sensitive details to the client.
    throw new Error('Could not retrieve customer data.');
  }
}
```

This is an example, not a complete production database layer. A real project should also validate IDs, manage connection lifecycle, configure timeouts, handle errors centrally, and avoid hiding useful diagnostic details from trusted server logs.

## Connection pool

A connection pool reuses a set of database connections instead of opening a brand-new connection for every request. Pool sizes and timeouts should be configured for the database and application workload.

## ORM vs raw SQL

An **Object-Relational Mapper (ORM)** lets developers work with database records through programming-language objects. Examples include Prisma, Sequelize, TypeORM, and SQLAlchemy.

- Raw SQL gives direct control over queries.
- An ORM can speed up common application tasks and provide structured data access.
- An ORM does not remove the need to understand SQL, database design, indexes, transactions, or query performance.

---

# 37. A Practical Company Database Project

Now build a small relational database for a company and an online shop. The following schema will be used in examples throughout the guide.

> **Database note:** The table definitions below use ordinary integer IDs so that you can insert the sample IDs explicitly. This keeps the script easy to adapt. In a real system, you may choose generated identity columns instead.

## Step 1: Create the tables

Run the script in a new, empty practice database. Create parent tables before child tables so their foreign keys can be created successfully.

```sql
CREATE TABLE departments (
    department_id INT PRIMARY KEY,
    department_name VARCHAR(100) NOT NULL UNIQUE
);

CREATE TABLE employees (
    employee_id INT PRIMARY KEY,
    employee_name VARCHAR(100) NOT NULL,
    email VARCHAR(150) UNIQUE,
    salary DECIMAL(10, 2) NOT NULL CHECK (salary >= 0),
    hire_date DATE NOT NULL,
    department_id INT,
    manager_id INT,
    FOREIGN KEY (department_id) REFERENCES departments(department_id),
    FOREIGN KEY (manager_id) REFERENCES employees(employee_id)
);

CREATE TABLE customers (
    customer_id INT PRIMARY KEY,
    customer_name VARCHAR(100) NOT NULL,
    email VARCHAR(150) NOT NULL UNIQUE,
    city VARCHAR(100),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE products (
    product_id INT PRIMARY KEY,
    product_name VARCHAR(120) NOT NULL,
    category VARCHAR(80) NOT NULL,
    price DECIMAL(10, 2) NOT NULL CHECK (price >= 0),
    stock_quantity INT NOT NULL DEFAULT 0 CHECK (stock_quantity >= 0)
);

CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    customer_id INT NOT NULL,
    order_date DATE NOT NULL,
    status VARCHAR(20) NOT NULL DEFAULT 'pending',
    FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
);

CREATE TABLE order_items (
    order_item_id INT PRIMARY KEY,
    order_id INT NOT NULL,
    product_id INT NOT NULL,
    quantity INT NOT NULL CHECK (quantity > 0),
    unit_price DECIMAL(10, 2) NOT NULL CHECK (unit_price >= 0),
    FOREIGN KEY (order_id) REFERENCES orders(order_id),
    FOREIGN KEY (product_id) REFERENCES products(product_id),
    UNIQUE (order_id, product_id)
);
```

The `employees.manager_id` foreign key references another employee in the same table. This is an example of a self-referencing relationship.

## Step 2: Insert sample data

```sql
INSERT INTO departments (department_id, department_name)
VALUES
    (1, 'Engineering'),
    (2, 'Marketing'),
    (3, 'Human Resources');

INSERT INTO employees
    (employee_id, employee_name, email, salary, hire_date, department_id, manager_id)
VALUES
    (1, 'Ayesha Rahman', 'ayesha@company.test', 85000, DATE '2022-03-10', 1, NULL),
    (2, 'Rahim Ahmed', 'rahim@company.test', 62000, DATE '2023-01-15', 1, 1),
    (3, 'Nila Islam', 'nila@company.test', 58000, DATE '2023-06-20', 2, NULL),
    (4, 'Tanvir Hasan', 'tanvir@company.test', 45000, DATE '2024-02-01', 2, 3),
    (5, 'Mim Akter', 'mim@company.test', 50000, DATE '2024-07-12', 3, NULL);

INSERT INTO customers (customer_id, customer_name, email, city)
VALUES
    (1, 'Sadia Khan', 'sadia@example.com', 'Dhaka'),
    (2, 'Fahim Chowdhury', 'fahim@example.com', 'Chattogram'),
    (3, 'Nusrat Jahan', 'nusrat@example.com', 'Dhaka'),
    (4, 'Imran Hossain', 'imran@example.com', 'Rajshahi');

INSERT INTO products (product_id, product_name, category, price, stock_quantity)
VALUES
    (1, 'Mechanical Keyboard', 'Accessories', 75.00, 20),
    (2, 'Wireless Mouse', 'Accessories', 25.00, 50),
    (3, 'Full HD Monitor', 'Displays', 180.00, 12),
    (4, 'USB-C Hub', 'Accessories', 45.00, 30),
    (5, 'Laptop Stand', 'Office', 35.00, 0);

INSERT INTO orders (order_id, customer_id, order_date, status)
VALUES
    (101, 1, DATE '2026-01-10', 'completed'),
    (102, 1, DATE '2026-01-15', 'completed'),
    (103, 2, DATE '2026-02-02', 'pending'),
    (104, 3, DATE '2026-02-05', 'completed');

INSERT INTO order_items
    (order_item_id, order_id, product_id, quantity, unit_price)
VALUES
    (1, 101, 1, 1, 75.00),
    (2, 101, 2, 2, 25.00),
    (3, 102, 3, 1, 180.00),
    (4, 103, 4, 2, 45.00),
    (5, 104, 2, 1, 25.00),
    (6, 104, 4, 1, 45.00);
```

## Step 3: Explore the data

```sql
SELECT * FROM departments;
SELECT * FROM employees;
SELECT * FROM customers;
SELECT * FROM products;
SELECT * FROM orders;
SELECT * FROM order_items;
```

## Step 4: Beginner queries

Find all products:

```sql
SELECT product_name, price
FROM products;
```

Find products that cost at least 50:

```sql
SELECT product_name, price
FROM products
WHERE price >= 50
ORDER BY price DESC;
```

Find customers in Dhaka:

```sql
SELECT customer_name, email
FROM customers
WHERE city = 'Dhaka';
```

Find products that are out of stock:

```sql
SELECT product_name
FROM products
WHERE stock_quantity = 0;
```

## Step 5: Intermediate queries

Count customers in each city:

```sql
SELECT city, COUNT(*) AS customer_count
FROM customers
GROUP BY city
ORDER BY customer_count DESC;
```

Find each customer's orders:

```sql
SELECT c.customer_name,
       o.order_id,
       o.order_date,
       o.status
FROM customers AS c
JOIN orders AS o
    ON c.customer_id = o.customer_id
ORDER BY o.order_date;
```

Calculate the total value of each order:

```sql
SELECT o.order_id,
       SUM(oi.quantity * oi.unit_price) AS order_total
FROM orders AS o
JOIN order_items AS oi
    ON o.order_id = oi.order_id
GROUP BY o.order_id
ORDER BY o.order_id;
```

Find customers who have not placed an order:

```sql
SELECT c.customer_id, c.customer_name
FROM customers AS c
LEFT JOIN orders AS o
    ON c.customer_id = o.customer_id
WHERE o.order_id IS NULL;
```

Find the average salary by department:

```sql
SELECT d.department_name,
       AVG(e.salary) AS average_salary
FROM departments AS d
JOIN employees AS e
    ON d.department_id = e.department_id
GROUP BY d.department_id, d.department_name;
```

## Step 6: Advanced queries

Rank employees by salary inside each department:

```sql
SELECT employee_name,
       department_id,
       salary,
       DENSE_RANK() OVER (
           PARTITION BY department_id
           ORDER BY salary DESC
       ) AS department_salary_rank
FROM employees;
```

Find products priced above the average product price:

```sql
SELECT product_name, price
FROM products
WHERE price > (SELECT AVG(price) FROM products);
```

Create a reusable order summary using a CTE:

```sql
WITH order_totals AS (
    SELECT order_id,
           SUM(quantity * unit_price) AS total_amount
    FROM order_items
    GROUP BY order_id
)
SELECT o.order_id,
       c.customer_name,
       o.status,
       ot.total_amount
FROM orders AS o
JOIN customers AS c
    ON c.customer_id = o.customer_id
JOIN order_totals AS ot
    ON ot.order_id = o.order_id
ORDER BY ot.total_amount DESC;
```

## Step 7: Add an index for a common lookup

```sql
CREATE INDEX idx_orders_customer_id
ON orders(customer_id);
```

Then inspect a query plan using your database's `EXPLAIN` command.

## Step 8: Project tasks

Try to build these features without looking at the answers first:

1. List all employees with their department names.
2. Find the highest-paid employee.
3. Find the second-highest distinct salary.
4. Calculate the number of orders per customer, including customers with zero orders.
5. Find the top three products by total quantity sold.
6. Calculate monthly sales totals.
7. Find products that have never been ordered.
8. Find departments with an average salary above 55,000.
9. Rank products by price inside each category.
10. Create a view showing each order and its total amount.

---

# 38. Practice Questions with Answers

Try each question first. The answer is directly below it so you can check your work.

## Beginner level

### 1. Display every column from the `customers` table.

```sql
SELECT * FROM customers;
```

### 2. Display only customer names and cities.

```sql
SELECT customer_name, city
FROM customers;
```

### 3. Find products costing more than 40.

```sql
SELECT *
FROM products
WHERE price > 40;
```

### 4. Find orders with a `completed` status.

```sql
SELECT *
FROM orders
WHERE status = 'completed';
```

### 5. Show products from highest price to lowest price.

```sql
SELECT product_name, price
FROM products
ORDER BY price DESC;
```

### 6. Find customers who live in Dhaka or Rajshahi.

```sql
SELECT *
FROM customers
WHERE city IN ('Dhaka', 'Rajshahi');
```

### 7. Count all customers.

```sql
SELECT COUNT(*) AS total_customers
FROM customers;
```

## Intermediate level

### 8. Find the average product price.

```sql
SELECT AVG(price) AS average_price
FROM products;
```

### 9. Count employees in each department.

```sql
SELECT department_id, COUNT(*) AS employee_count
FROM employees
GROUP BY department_id;
```

### 10. Display employees with department names.

```sql
SELECT e.employee_name, d.department_name
FROM employees AS e
JOIN departments AS d
    ON e.department_id = d.department_id;
```

### 11. Find customers with no orders.

```sql
SELECT c.customer_id, c.customer_name
FROM customers AS c
LEFT JOIN orders AS o
    ON c.customer_id = o.customer_id
WHERE o.order_id IS NULL;
```

### 12. Find customers who placed more than one order.

```sql
SELECT customer_id, COUNT(*) AS order_count
FROM orders
GROUP BY customer_id
HAVING COUNT(*) > 1;
```

### 13. Show the total quantity sold for each product.

```sql
SELECT p.product_id,
       p.product_name,
       COALESCE(SUM(oi.quantity), 0) AS quantity_sold
FROM products AS p
LEFT JOIN order_items AS oi
    ON p.product_id = oi.product_id
GROUP BY p.product_id, p.product_name
ORDER BY quantity_sold DESC;
```

## Advanced level

### 14. Find employees who earn more than the average salary.

```sql
SELECT employee_name, salary
FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```

### 15. Find the second-highest distinct salary.

```sql
SELECT MAX(salary) AS second_highest_salary
FROM employees
WHERE salary < (SELECT MAX(salary) FROM employees);
```

This returns `NULL` if there is no second distinct salary.

### 16. Rank employees by salary in each department.

```sql
SELECT employee_name,
       department_id,
       salary,
       DENSE_RANK() OVER (
           PARTITION BY department_id
           ORDER BY salary DESC
       ) AS salary_rank
FROM employees;
```

### 17. Find products that have never been ordered.

```sql
SELECT p.product_id, p.product_name
FROM products AS p
WHERE NOT EXISTS (
    SELECT 1
    FROM order_items AS oi
    WHERE oi.product_id = p.product_id
);
```

### 18. Calculate total sales for each customer.

```sql
SELECT c.customer_id,
       c.customer_name,
       COALESCE(SUM(oi.quantity * oi.unit_price), 0) AS total_spent
FROM customers AS c
LEFT JOIN orders AS o
    ON c.customer_id = o.customer_id
LEFT JOIN order_items AS oi
    ON o.order_id = oi.order_id
GROUP BY c.customer_id, c.customer_name
ORDER BY total_spent DESC;
```

### 19. Find each employee's manager.

```sql
SELECT e.employee_name AS employee,
       m.employee_name AS manager
FROM employees AS e
LEFT JOIN employees AS m
    ON e.manager_id = m.employee_id;
```

### 20. Return the top three products by sales revenue.

```sql
SELECT p.product_id,
       p.product_name,
       SUM(oi.quantity * oi.unit_price) AS revenue
FROM products AS p
JOIN order_items AS oi
    ON p.product_id = oi.product_id
GROUP BY p.product_id, p.product_name
ORDER BY revenue DESC
LIMIT 3;
```

`LIMIT` is not supported in every database system; use the equivalent syntax for your database.

---

# 39. Common SQL Interview Questions

## 1. What is SQL?

SQL is a language used to define, query, and manage data in relational database systems.

## 2. What is a database?

A database is an organised collection of data.

## 3. What is the difference between DBMS and RDBMS?

DBMS is a general term for database management software. An RDBMS is a relational database system that organises data into related tables and uses relational concepts such as keys and constraints.

## 4. What is a primary key?

A primary key uniquely identifies each row in a table and cannot contain `NULL`.

## 5. What is a foreign key?

A foreign key is a column or group of columns that references a key in another table (or the same table), helping enforce a relationship.

## 6. What is the difference between PRIMARY KEY and UNIQUE?

Both enforce uniqueness. A primary key also identifies the row and cannot be `NULL`. A table has one primary key constraint, while it can have multiple unique constraints. Handling of `NULL` in unique constraints varies by database.

## 7. What is the difference between DELETE, TRUNCATE, and DROP?

`DELETE` removes rows, `TRUNCATE` removes all rows while keeping the table structure (with system-specific behaviour), and `DROP` removes the table object itself.

## 8. What is the difference between WHERE and HAVING?

`WHERE` filters rows before grouping. `HAVING` filters groups after `GROUP BY`.

## 9. What is the difference between INNER JOIN and LEFT JOIN?

`INNER JOIN` returns matching rows. `LEFT JOIN` returns all rows from the left table and matching rows from the right table, using `NULL` for missing matches.

## 10. What is normalization?

Normalization organises data into related tables to reduce unnecessary duplication and data anomalies.

## 11. What is an index?

An index is a data structure that can speed up data retrieval for some queries, at the cost of storage and extra work when data changes.

## 12. What is a view?

A view is a saved query that can be read like a virtual table.

## 13. What is a transaction?

A transaction is a group of database operations treated as one unit of work.

## 14. What does ACID mean?

Atomicity, Consistency, Isolation, and Durability.

## 15. What is a subquery?

A query nested inside another SQL statement.

## 16. What is a CTE?

A Common Table Expression is a named query result defined with `WITH` for use in one statement.

## 17. What is a window function?

A window function calculates a value across related rows while generally keeping each row in the output.

## 18. What is SQL injection?

SQL injection is a security problem where unsafe input changes the meaning of a SQL statement. Parameterized queries help prevent it.

## 19. What is the difference between UNION and UNION ALL?

`UNION` removes duplicate rows; `UNION ALL` keeps them.

## 20. What is the difference between COUNT(*) and COUNT(column)?

`COUNT(*)` counts rows. `COUNT(column)` counts non-`NULL` values in that column.

---

# 40. Common Beginner Mistakes

1. **Forgetting `WHERE` in an update or delete.** This can change or remove every row.
2. **Using `= NULL`.** Use `IS NULL` instead.
3. **Mixing `AND` and `OR` without parentheses.** Make the intended logic explicit.
4. **Joining tables on the wrong columns.** This can create incorrect results or duplicate rows.
5. **Using `SELECT *` everywhere.** Select only the columns needed in application queries.
6. **Forgetting `GROUP BY`.** Non-aggregated selected columns generally need to be part of the grouping, subject to database-specific rules.
7. **Using `WHERE` for aggregate filters.** Use `HAVING` for conditions on grouped aggregate results.
8. **Assuming row order is guaranteed.** Use `ORDER BY` when order matters.
9. **Assuming every SQL database has identical syntax.** Learn your database's dialect.
10. **Storing money in floating-point columns.** Prefer exact decimal types for monetary amounts.
11. **Building SQL by concatenating user input.** Use parameterized queries.
12. **Adding indexes without measuring.** An index is not always useful and can slow down writes.
13. **Ignoring backups.** Test restore procedures, not only backup creation.
14. **Using overly broad database permissions.** Follow least privilege.
15. **Not testing on sample data first.** Practise destructive operations in a safe environment.

---

# 41. SQL Best Practices

- Use clear, consistent table and column names. Choose `snake_case` or another style and keep it consistent.
- Use singular or plural table names consistently; either can work when the team agrees.
- Give every table a reliable primary key.
- Use foreign keys and constraints to protect data integrity.
- Choose suitable data types.
- Use `NOT NULL`, `UNIQUE`, `CHECK`, and `DEFAULT` where they represent real business rules.
- Use parameterized queries for application input.
- Never commit database passwords or API credentials to GitHub.
- Use transactions for multi-step operations that must succeed together.
- Review `UPDATE` and `DELETE` conditions before executing them.
- Add indexes based on measured query patterns.
- Use `EXPLAIN` and performance measurements to understand slow queries.
- Keep backups and regularly test restoration.
- Use separate database accounts for applications, reporting, and administration when appropriate.
- Avoid storing the same fact in many places unless there is a deliberate, documented design reason.
- Document complex queries and important business rules.
- Test schema changes and migrations before applying them to production.

---

# 42. SQL Command Cheat Sheet

| Goal | SQL |
|---|---|
| Create a database | `CREATE DATABASE database_name;` |
| Create a table | `CREATE TABLE table_name (...);` |
| Insert data | `INSERT INTO table_name (...) VALUES (...);` |
| Read data | `SELECT column FROM table_name;` |
| Filter rows | `SELECT ... FROM ... WHERE condition;` |
| Sort rows | `ORDER BY column ASC;` |
| Remove duplicates | `SELECT DISTINCT column FROM table_name;` |
| Limit rows | `LIMIT 10;` (system-dependent) |
| Update data | `UPDATE table_name SET column = value WHERE condition;` |
| Delete rows | `DELETE FROM table_name WHERE condition;` |
| Add a column | `ALTER TABLE table_name ADD COLUMN column_name data_type;` |
| Remove a table | `DROP TABLE table_name;` |
| Count rows | `SELECT COUNT(*) FROM table_name;` |
| Sum values | `SELECT SUM(column) FROM table_name;` |
| Group rows | `GROUP BY column;` |
| Filter groups | `HAVING aggregate_condition;` |
| Join tables | `SELECT ... FROM a JOIN b ON a.id = b.id;` |
| Create a view | `CREATE VIEW view_name AS SELECT ...;` |
| Create an index | `CREATE INDEX index_name ON table_name(column);` |
| Begin a transaction | `BEGIN;` |
| Save a transaction | `COMMIT;` |
| Cancel uncommitted changes | `ROLLBACK;` |
| Explain a query plan | `EXPLAIN SELECT ...;` |

## Main SQL command categories

These categories are commonly used for learning. Exact classification can vary between references and database products.

| Category | Full form | Common commands | Purpose |
|---|---|---|---|
| DDL | Data Definition Language | `CREATE`, `ALTER`, `DROP`, `TRUNCATE` | Define or change database objects |
| DML | Data Manipulation Language | `INSERT`, `UPDATE`, `DELETE`, `MERGE` | Change table data |
| DQL | Data Query Language | `SELECT` | Read/query data |
| DCL | Data Control Language | `GRANT`, `REVOKE` | Manage permissions |
| TCL | Transaction Control Language | `COMMIT`, `ROLLBACK`, `SAVEPOINT` | Manage transactions |

---

# 43. SQL Learning Roadmap

Follow this order for a steady learning path.

## Level 1: Foundations

Learn:

- What databases, DBMSs, RDBMSs, tables, rows, and columns are.
- SQL syntax and comments.
- Data types.
- `CREATE TABLE`, `INSERT`, and `SELECT`.
- `WHERE`, comparison operators, `AND`, `OR`, and `NOT`.
- `ORDER BY`, `LIMIT`, and `DISTINCT`.

**Goal:** Create a small table, insert data, and query it confidently.

## Level 2: Core SQL

Learn:

- `UPDATE` and `DELETE`.
- Constraints and keys.
- `NULL`, `LIKE`, `IN`, and `BETWEEN`.
- Functions and aliases.
- Aggregate functions.
- `GROUP BY` and `HAVING`.

**Goal:** Search, change, summarise, and validate data.

## Level 3: Relational SQL

Learn:

- One-to-one, one-to-many, and many-to-many relationships.
- `INNER`, `LEFT`, `RIGHT`, `FULL`, `CROSS`, and self joins.
- Subqueries and `EXISTS`.
- `UNION` and `UNION ALL`.
- Normalization and relational database design.

**Goal:** Design related tables and combine their data accurately.

## Level 4: Professional SQL

Learn:

- Views and indexes.
- Transactions and ACID.
- CTEs and recursive CTEs.
- Window functions.
- Query plans and performance tuning.
- Backup and restore basics.

**Goal:** Write readable queries and understand data integrity and performance.

## Level 5: Advanced and production skills

Learn:

- Stored procedures, functions, and triggers.
- Permissions and least privilege.
- Parameterized queries and SQL injection prevention.
- Migrations and schema versioning.
- Connection pools and application integration.
- Monitoring, backups, recovery, and operational safety.
- Your chosen database system's advanced features.

**Goal:** Use SQL safely in a real application.

## Suggested practice routine

- Read one topic.
- Type the examples yourself instead of only copying them.
- Predict what each query will return.
- Run it and compare the result.
- Change one condition and run it again.
- Solve the practice questions without looking at the answers.
- Build the company database project and add your own features.

A good learner does not only memorise SQL commands. A good learner understands the data, the relationships, the result, and the reason behind each query.

---

# 44. Glossary

| Term | Simple meaning |
|---|---|
| Aggregate function | A function that calculates a result from multiple rows |
| Alias | A temporary name for a table or output column |
| Atomicity | A transaction succeeds as a unit or is rolled back |
| Backup | A copy of data used for recovery |
| Candidate key | A minimal column set that uniquely identifies a row |
| Constraint | A rule that protects data validity |
| Correlated subquery | A subquery that refers to the outer query |
| CTE | A named query result created with `WITH` |
| Database | An organised collection of data |
| DBMS | Software used to manage databases |
| Denormalization | Deliberately adding some duplication to meet a measured design or performance need |
| Foreign key | A key that references a key in another table |
| Index | A data structure that can speed up some data lookups |
| Join | An operation that combines related rows from tables |
| Normalization | Organising data to reduce unnecessary duplication and anomalies |
| NULL | A missing or unknown value |
| Primary key | The key that identifies each row in a table |
| Query | A request or command sent to a database |
| RDBMS | A relational database management system |
| Referential integrity | The consistency of references between related tables |
| Row | One record in a table |
| Schema | The structure and objects of a database |
| SQL | Structured Query Language |
| Subquery | A query inside another query |
| Transaction | A group of operations treated as one unit |
| Trigger | A database routine that runs automatically for a configured event |
| View | A saved query that can be queried like a virtual table |
| Window function | A function that calculates across related rows while keeping row-level output |

---

## Final Advice

SQL becomes easy when you practise it consistently. Start with `SELECT`, `WHERE`, and `ORDER BY`. Then learn joins, grouping, subqueries, and database design. After that, move to transactions, indexes, CTEs, window functions, security, and application integration.

**Do not only read this README. Open a database, type every example, make mistakes, fix them, and build something real.**

Happy learning, and keep practising SQL!
