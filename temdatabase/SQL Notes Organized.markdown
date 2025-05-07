
## Introduction to Databases

A **database** is a collection of data in a digital format that can be easily accessed. A **Database Management System (DBMS)** is a software application used to manage databases.

![DBMS Flow](https://github.com/Khalil-Haider/database_course/raw/main/assets_image/DBMS%20flow_clear.PNG)

## Types of Databases


![types of Database](https://github.com/Khalil-Haider/database_course/raw/main/assets_image/types%20of%20dtabasegif.gif)

![Types of Database](https://github.com/Khalil-Haider/database_course/raw/main/assets_image/types%20of%20database_.gif)


- **Relational Databases**: Data is stored in tables.
  - Examples: PostgreSQL also known as Postgres,MySQL, Microsoft SQL Server.
  

## What is SQL?

**Structured Query Language (SQL)** is a programming language used to interact with relational databases. It supports **CRUD operations**:
- **Create**: Add new data.
- **Read**: Retrieve data.
- **Update**: Modify existing data.
- **Delete**: Remove data.

## Database Structure

A database contains multiple tables, each holding data in a structured format (rows and columns).

**Example**:
- Database
  - Table 1
  - Table 2
  - Data (rows and columns)

## Tables

A **table** is a collection of rows and columns storing data. For example, a **Student table** might look like:

| rollno | name     | marks | grade | city   |
|--------|----------|-------|-------|--------|
| 101    | anil     | 78    | C     | Pune   |
| 102    | bhumika  | 93    | A     | Mumbai |


![table structure ](https://github.com/Khalil-Haider/database_course/raw/main/assets_image/table_database_overview.PNG)
## Creating a Database

**Syntax**:
```sql
CREATE DATABASE db_name;
DROP DATABASE db_name;
```

**Example**:
```sql
CREATE DATABASE college;
DROP DATABASE college;
```

## Creating a Table

**Syntax**:
```sql
USE db_name;
CREATE TABLE table_name (
    column_name1 datatype constraint,
    column_name2 datatype constraint,
    column_name3 datatype constraint
);
```

**Example**:
```sql
USE college;
CREATE TABLE student (
    rollno INT PRIMARY KEY,
    name VARCHAR(50),
    marks INT NOT NULL,
    grade VARCHAR(1),
    city VARCHAR(20)
);
```

## SQL Datatypes

Datatypes define the type of values a column can store.

| **Datatype** | **Description**                                                                 | **Usage**         |
|--------------|---------------------------------------------------------------------------------|--------------------|
| CHAR         | Fixed-length string (0-255 characters)                                          | CHAR(50)          |
| VARCHAR      | Variable-length string (0-255 characters)                                       | VARCHAR(50)       |
| BLOB         | Binary large object (0-65535 characters)                                        | BLOB(1000)        |
| INT          | Integer (-2,147,483,648 to 2,147,483,647)                                       | INT               |
| TINYINT      | Integer (-128 to 127)                                                           | TINYINT           |
| BIGINT       | Integer (-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807)               | BIGINT            |
| BIT          | Stores x-bit values (1 to 64)                                                   | BIT(2)            |
| FLOAT        | Decimal number with precision up to 23 digits                                   | FLOAT             |
| DOUBLE       | Decimal number with 24 to 53 digits                                             | DOUBLE            |
| BOOLEAN      | Stores 0 or 1                                                                   | BOOLEAN           |
| DATE         | Date in YYYY-MM-DD format (1000-01-01 to 9999-12-31)                           | DATE              |
| YEAR         | Year in 4-digit format (1901 to 2155)                                          | YEAR              |

**Signed vs. Unsigned**:
- `TINYINT UNSIGNED`: 0 to 255.

## Types of SQL Commands

![SQL Commands](https://github.com/Khalil-Haider/database_course/raw/main/assets_image/sql_commands.svg)



## Database Queries

**Examples**:
```sql
CREATE DATABASE college;
CREATE DATABASE IF NOT EXISTS college;
```

## Table Queries

### Create Table
```sql
CREATE TABLE student (
    rollno INT PRIMARY KEY,
    name VARCHAR(50)
);
```

### Select All Columns
```sql
SELECT * FROM student;
```

### Insert Data
```sql
INSERT INTO student (rollno, name)
VALUES
    (101, 'karan'),
    (102, 'arjun');
```

## Keys

<p align="center">
  <img src="https://github.com/Khalil-Haider/database_course/raw/main/assets_image/Types-of-Keys-in-Database.PNG" alt="Types of keys" width="800px">
</p>


- **Primary Key (PK)**: Uniquely identifies each row, only one per table, cannot be NULL.
- **Foreign Key (FK)**: Refers to the primary key in another table, can have duplicates and NULL values.

<details>
<summary>▶️ Click to view detailed database keys</summary>

---

![keys in depth](https://github.com/Khalil-Haider/database_course/raw/main/assets_image/index.svg)

---

</details>



**Example**:
```sql
CREATE TABLE student (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    cityId INT,
    FOREIGN KEY (cityId) REFERENCES city(id)
);
```

**Sample Tables**:

**Student**:
| id  | name   | cityId |
|-----|--------|--------|
| 101 | karan  | 1      |
| 102 | arjun  | 2      |
| 103 | ram    | 1      |
| 104 | shyam  | 3      |

**City**:
| id  | city_name |
|-----|-----------|
| 1   | Pune      |
| 2   | Mumbai    |
| 3   | Delhi     |

## Constraints
<p align="center">
  <img src="https://github.com/Khalil-Haider/database_course/raw/main/assets_image/constraints.svg" alt="Clause" width="800px">
</p>
                          |

**Examples**:
```sql
CREATE TABLE temp (
    id INT NOT NULL,
    PRIMARY KEY (id)
);

CREATE TABLE city (
    id INT PRIMARY KEY,
    city VARCHAR(50),
    age INT,
    CONSTRAINT age_check CHECK (age >= 18 AND city = 'Delhi')
);
```

## Sample Table Creation and Data Insertion

**წ

**SQL Commands**:
```sql
CREATE DATABASE college;
USE college;
CREATE TABLE student (
    rollno INT PRIMARY KEY,
    name VARCHAR(50),
    marks INT NOT NULL,
    grade VARCHAR(1),
    city VARCHAR(20)
);
INSERT INTO student (rollno, name, marks, grade, city)
VALUES
    (101, 'anil', 78, 'C', 'Pune'),
    (102, 'bhumika', 93, 'A', 'Mumbai'),
    (103, 'chetan', 85, 'B', 'Mumbai'),
    (104, 'dhruv', 96, 'A', 'Delhi'),
    (105, 'emanuel', 12, 'F', 'Delhi'),
    (106, 'farah', 82, 'B', 'Delhi');
```

## SELECT Queries

### Basic SELECT
```sql
SELECT rollno, name FROM student;
```
# Clause 

<p align="center">
  <img src="https://github.com/Khalil-Haider/database_course/raw/main/assets_image/clause_.svg" alt="Clause" width="800px">
</p>


# What is Clause?

A clause in SQL is a part of a query that performs a specific task like selecting, filtering, grouping, sorting, or limiting data.

| Clause Name | Description | Example Query |
|:-----------|:-------------|:--------------|
| **SELECT / DISTINCT** | Retrieves one or more columns. `DISTINCT` removes duplicate values. | `SELECT DISTINCT col_name FROM table_name;` |
| **FROM** | Specifies the table to get data from. | `SELECT col_name FROM table_name;` |
| **WHERE** | Filters rows based on a condition. | `SELECT col_name FROM table_name WHERE col_name > 100;` |
| **GROUP BY** | Groups rows with the same values in a column. | `SELECT col_name FROM table_name GROUP BY col_name;` |
| **HAVING** | Filters groups after grouping data. | `SELECT col_name FROM table_name GROUP BY col_name HAVING col_name > 100;` |
| **ORDER BY** | Sorts the rows based on one or more columns. | `SELECT col_name FROM table_name ORDER BY col_name ASC;` |
| **LIMIT / OFFSET** | Limits the number of rows and skips rows. | `SELECT col_name FROM table_name LIMIT 10 OFFSET 5;` |



### WHERE Clause

<p align="center">
  <img src="https://github.com/Khalil-Haider/database_course/raw/main/assets_image/where_clause.svg" alt="where clause" width="800px">
</p>

```sql
SELECT * FROM student WHERE marks > 80;
SELECT * FROM student WHERE city = 'Mumbai';
```

### Operators in WHERE
- **Arithmetic**: `+`, `-`, `*`, `/`, `%`
- **Comparison**: `=`, `!=`, `>`, `>=`, `<`, `<=`
- **Logical**: `AND`, `OR`, `NOT`, `IN`, `BETWEEN`, `LIKE`, `ANY`
- **Bitwise**: `&`, `|`

**Examples**:
```sql
SELECT * FROM student WHERE marks > 80 AND city = 'Mumbai';
SELECT * FROM student WHERE marks > 90 OR city = 'Mumbai';
SELECT * FROM student WHERE marks BETWEEN 80 AND 90;
SELECT * FROM student WHERE city IN ('Delhi', 'Mumbai');
```

### LIMIT Clause
```sql
SELECT * FROM student LIMIT 3;
```
<p align="center">
  <img src="https://github.com/Khalil-Haider/database_course/raw/main/assets_image/limit_offset.svg" alt="limit offset" width="700px">
</p>


### ORDER BY Clause
```sql
SELECT * FROM student ORDER BY city ASC;
```
# Other Operator

<p align="center">
  <img src="https://github.com/Khalil-Haider/database_course/raw/main/assets_image/pattern_match_like_ilike.svg" alt="Like vs Ilike" width="700px">
</p>

# Pattern Rules 

<p align="center">
  <img src="https://github.com/Khalil-Haider/database_course/raw/main/assets_image/pattern_matching_like.PNG" alt="attern rules" width="700px">
</p>

# String Function 


### Aggregate Functions
- `COUNT()`: Counts rows.
- `MAX()`: Finds maximum value.
- `MIN()`: Finds minimum value.
- `SUM()`: Calculates sum.
- `AVG()`: Calculates average.

**Example**:
```sql
SELECT COUNT(*) FROM student;
SELECT MAX(marks) FROM student;
```

### GROUP BY Clause
```sql
SELECT city, COUNT(name)
FROM student
GROUP BY city;
```

### HAVING Clause
```sql
SELECT COUNT(name), city
FROM student
GROUP BY city
HAVING MAX(marks) > 90;
```

### General Order of Clauses
```sql
SELECT column(s)
FROM table_name
WHERE condition
GROUP BY column(s)
HAVING condition
ORDER BY column(s) ASC;
```

## Table Modifications

### UPDATE
```sql
UPDATE student
SET grade = 'O'
WHERE grade = 'A';
```

### DELETE
```sql
DELETE FROM student
WHERE marks < 50;
```

### ALTER
```sql
ALTER TABLE student
ADD COLUMN age INT NOT NULL DEFAULT 19;

ALTER TABLE student
MODIFY age VARCHAR(2);

ALTER TABLE student
CHANGE age stu_age INT;

ALTER TABLE student
DROP COLUMN stu_age;

ALTER TABLE student
RENAME TO stu;
```

### TRUNCATE
```sql
TRUNCATE TABLE student;
```
![delete drop truncate ](https://github.com/Khalil-Haider/database_course/raw/main/assets_image/delete_vs_truncate_drop.svg)
## Cascading for Foreign Keys

- **ON DELETE CASCADE**: Deletes child table rows when the parent table row is deleted.
- **ON UPDATE CASCADE**: Updates child table rows when the parent table row is updated.

**Example**:
```sql
CREATE TABLE student (
    id INT PRIMARY KEY,
    courseID INT,
    FOREIGN KEY (courseID) REFERENCES course(id)
    ON DELETE CASCADE
    ON UPDATE CASCADE
);
```

## Joins

Joins combine rows from multiple tables based on a related column.

<p align="center">
  <img src="https://github.com/Khalil-Haider/database_course/raw/main/assets_image/sql%20join.gif" alt="joins" width="800px">
</p>


### Types of Joins
- **Inner Join**: Returns matching records from both tables.
- **Left Join**: Returns all records from the left table and matching records from the right.
- **Right Join**: Returns all records from the right table and matching records from the left.
- **Full Join**: Returns all records when there is a match in either table.
- **Self Join**: Joins a table with itself.

**Examples**:

#### Inner Join
```sql
SELECT *
FROM student AS s
INNER JOIN course AS c
ON s.student_id = c.student_id;
```

**Sample Data**:
**Student**:
| student_id | name   |
|------------|--------|
| 101        | adam   |
| 102        | bob    |
| 103        | casey  |

**Course**:
| student_id | course            |
|------------|-------------------|
| 102        | english           |
| 105        | math              |
| 103        | science           |
| 107        | computer science  |

**Result**:
| student_id | name  | course  |
|------------|-------|---------|
| 102        | bob   | english |
| 103        | casey | science |

#### Left Join
```sql
SELECT *
FROM student AS s
LEFT JOIN course AS c
ON s.student_id = c.student_id;
```

**Result**:
| student_id | name  | course  |
|------------|-------|---------|
| 101        | adam  | NULL    |
| 102        | bob   | english |
| 103        | casey | science |

#### Right Join
```sql
SELECT *
FROM student AS s
RIGHT JOIN course AS c
ON s.student_id = c.student_id;
```

**Result**:
| student_id | name  | course            |
|------------|-------|-------------------|
| 102        | bob   | english           |
| 103        | casey | science           |
| 105        | NULL  | math              |
| 107        | NULL  | computer science  |

#### Full Join
```sql
SELECT *
FROM student AS s
LEFT JOIN course AS c
ON s.student_id = c.student_id
UNION
SELECT *
FROM student AS s
RIGHT JOIN course AS c
ON s.student_id = c.student_id;
```

**Result**:
| student_id | name  | course            |
|------------|-------|-------------------|
| 101        | adam  | NULL              |
| 102        | bob   | english           |
| 103        | casey | science           |
| 105        | NULL  | math              |
| 107        | NULL  | computer science  |

#### Self Join
```sql
SELECT a.name AS manager_name, b.name
FROM employee AS a
JOIN employee AS b
ON a.id = b.manager_id;
```

**Sample Data**:
**Employee**:
| id  | name   | manager_id |
|-----|--------|------------|
| 101 | adam   | 103        |
| 102 | bob    | 104        |
| 103 | casey  | NULL       |
| 104 | donald | 103        |

**Result**:
| manager_name | name   |
|--------------|--------|
| casey        | adam   |
| donald       | bob    |
| casey        | donald |

## UNION
Combines the result-set of two or more SELECT statements, returning unique records.

**Syntax**:
```sql
SELECT column(s) FROM tableA
UNION
SELECT column(s) FROM tableB;
```

**Rules**:
- Same number of columns.
- Similar data types.
- Columns in the same order.

# Union vs Join

![Union vs Join](https://github.com/Khalil-Haider/database_course/raw/main/assets_image/union%20vs%20join.PNG)

## Subqueries

A **subquery** is a query nested within another SQL query.

![subquery](https://github.com/Khalil-Haider/database_course/raw/main/assets_image/subquery.jpg)
**Examples**:

### Students with Marks Above Class Average
```sql
SELECT name
FROM student
WHERE marks > (SELECT AVG(marks) FROM student);
```

### Students with Even Roll Numbers
```sql
SELECT name
FROM student
WHERE rollno IN (SELECT rollno FROM student WHERE rollno % 2 = 0);
```

### Max Marks from Students in Delhi
```sql
SELECT MAX(marks)
FROM student
WHERE city = 'Delhi';
```

## MySQL Views

A **view** is a virtual table based on the result of an SQL statement.

**Syntax**:
```sql
CREATE VIEW view1 AS
    SELECT rollno, name FROM student;
SELECT * FROM view1;
```

**Note**: Views are updated automatically when the underlying table data changes.

![view](https://github.com/Khalil-Haider/database_course/raw/main/assets_image/view.png)

---

## 📌 What is an Index?

- An **index** improves database performance by allowing faster retrieval of specific rows.
- It organizes data to speed up queries but can **slow down** data modification operations if overused.

---


# Guidelines for Using Indexes in PostgreSQL

## 📌 General Guidelines

- **Primary Keys and Unique Constraints**:  
  PostgreSQL automatically creates indexes for `PRIMARY KEY` and `UNIQUE` columns.

- **Frequent Retrieval Columns**:  
  Create indexes on columns that are often used in `SELECT` queries to retrieve data.

- **Join Columns**:  
  Index the columns that are commonly used in `JOIN` operations to improve join performance.

- **Avoid High NULL Columns**:  
  Avoid creating indexes on columns that have too many `NULL` values, as it can degrade performance.

- **Small Tables**:  
  Small tables generally **do not** require indexes because full table scans are already fast.

- **Performance Balance**:  
  Indexes speed up data retrieval but add overhead to `INSERT`, `UPDATE`, and `DELETE` operations.  
  ➔ **Use indexes sensibly** to maintain overall database performance.



## 📌 Description of `CREATE INDEX`

| Topic | Details |
|:-----|:--------|
| **Purpose** | Enhance database performance by creating fast lookup structures. |
| **Syntax** | `CREATE INDEX index_name ON table_name (column_name);` |
| **Multiple Columns** | Index can be created on multiple columns if the method supports it. |
| **Expression Indexes** | You can create indexes based on expressions like `UPPER(column_name)`. |
| **Partial Indexes** | Use a `WHERE` clause to create an index on a subset of table data. |
| **Index Methods** | PostgreSQL supports `B-tree`, `Hash`, `GiST`, and `GIN` index types. |
| **Restrictions** | - `WHERE` clause can't use subqueries or aggregate functions. <br> - Functions used must be **IMMUTABLE** (outputs depend only on inputs). |

---

## 📌 Example Queries

### 1. Create a simple index
```sql
CREATE INDEX idx_student_name ON student(name);

```

# Video: Database Indexing

<video src="https://github.com/Khalil-Haider/database_course/raw/main/assets_image/DatabaseSearchComparison.mp4" controls width="600"></video>

# 📚 Stored Procedures in SQL

## 📌 What is a Stored Procedure?

A **Stored Procedure** in SQL is a collection of SQL statements that are **saved** and **stored** inside the database.  
It is used to perform a sequence of operations like:

- Querying data
- Inserting data
- Updating data
- Deleting data

Unlike regular SQL queries (which run one command at a time), a stored procedure encapsulates multiple SQL statements together, allowing you to **reuse** and **simplify** your database operations.

---

## 📌 Benefits of Using Stored Procedures

- **🔄 Code Reusability**:  
  Create once, call multiple times — reduces repetition of SQL code.

- **⚡ Enhanced Performance**:  
  Stored procedures are **precompiled** and stored on the server, making execution faster by reducing network communication and compilation time.

- **🔒 Security**:  
  You can allow users to **execute** a stored procedure without giving them direct access to database tables — improving **data protection**.

---

## 📌 Syntax of Stored Procedure (PostgreSQL Example)

```sql
CREATE OR REPLACE PROCEDURE procedure_name(parameters)
LANGUAGE plpgsql
AS $$
BEGIN
   -- SQL statements here
END;
$$;

```

![Store procedure](https://github.com/Khalil-Haider/database_course/raw/main/assets_image/store_procedure_define_1.jpg)


# 📚 Query vs Stored Procedure

| Feature            | Query | Stored Procedure |
|--------------------|:-----:|:----------------:|
| **Definition**      | One-time SQL request for data or updates. | Reusable, precompiled block of SQL stored in the database. |
| **Usage**           | Simple and great for quick, ad-hoc tasks. | Secure and consistent for repetitive tasks. |
| **Performance**     | Slower: Processed fresh every time. | Faster: Already optimized by the database. |

---

## 📌 Summary

- **Query**:  
  - Good for one-time, quick, or simple tasks.  
  - Each execution is processed individually.

- **Stored Procedure**:  
  - Best for repetitive, secured, and performance-critical operations.  
  - Stored, precompiled, and optimized by the database.


![query vs Store procedure](https://github.com/Khalil-Haider/database_course/raw/main/assets_image/Stored_Procedures_Vs_Simple%20Query.PNG)

# 🚀 Stored Procedure vs Python Code

| Feature            | Stored Procedure | Python Code |
|--------------------|:----------------:|:-----------:|
| **Performance**     | Faster because they’re precompiled. | Executes SQL dynamically (slightly slower). |
| **Flexibility**     | Limited to database operations. | Highly flexible — APIs, advanced logic, multiple databases. |
| **Version Control** | Hard to version control directly. | Easily fits into Git and other tools. |
| **Maintenance**     | Updating requires modifying the database. | Updating is simpler with modern coding tools. |
| **Complex Logic**   | Good for basic to moderate database tasks. | Excellent for complex logic and workflows using rich libraries. |

---

## 📌 Wrapping Up

- **Stored Procedures**:  
  - ✅ Fast  
  - ✅ Secure  
  - ❌ Less flexible  
  - ❌ Harder to maintain and version

- **Python Code**:  
  - ✅ Highly flexible and powerful  
  - ✅ Easy to maintain, update, and version  
  - ❌ Slightly slower compared to stored procedures

---

![Store Procedure vs python code ](https://github.com/Khalil-Haider/database_course/raw/main/assets_image/Stored_Procedures_Vs_python_code.PNG)



# Window Functions

```markdown
Window Functions work like GROUP BY but keep all rows visible

Using a window function prevents rows from being aggregated into a single output row

```

---

## 🧠 Basic Syntax of a Window Function

```sql
SELECT column_name,
       AGG_FUNCTION() OVER (PARTITION BY col ORDER BY col) AS new_column
FROM table_name;
````



![Window function vs Group by](https://github.com/Khalil-Haider/database_course/raw/main/assets_image/window%20function%20complete.PNG)

---

# Types of Window function

---

![Types of Window function ](https://github.com/Khalil-Haider/database_course/raw/main/assets_image/types%20of%20window%20function.PNG)

---

# Window Function Animation

---

<video controls src="https://github.com/Khalil-Haider/database_course/raw/main/assets_image/WindowFunctionsAnimation.mp4" title="Window Function Animation"></video>



## ✅ Tip:

Use window functions when you want row-level visibility **with aggregate-style power**, 

such as running totals, ranks, and percentiles.


```


