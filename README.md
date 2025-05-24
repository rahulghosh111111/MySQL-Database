
# 📘 MySQL Basics and Query Reference

This README provides a detailed explanation of **MySQL** queries, syntax, and examples using tables like `EMPLOYEE`, `PROJECT`, and `CLIENT`.

---

## 📦 Table of Contents
- [Database Basics](#-database-basics)
- [DDL (Data Definition Language)](#-ddl-data-definition-language)
- [DML (Data Manipulation Language)](#-dml-data-manipulation-language)
- [DQL (Data Query Language)](#-dql-data-query-language)
- [Joins](#-joins)
- [Aggregate Functions](#-aggregate-functions)
- [Filtering and Sorting](#-filtering-and-sorting)
- [Group By and Having](#-group-by-and-having)
- [Subqueries](#-subqueries)
- [Views](#-views)

---

## 🏗️ Database Basics

### Create a Database
```sql
CREATE DATABASE MULTIPLE_JOIN;
USE MULTIPLE_JOIN;
```

---

## 🛠️ DDL (Data Definition Language)

### Create Table
```sql
CREATE TABLE EMPLOYEE (
    id INT PRIMARY KEY,
    fname VARCHAR(100),
    lname VARCHAR(100),
    Age INT,
    emailID VARCHAR(100),
    PhoneNo VARCHAR(20),
    City VARCHAR(100)
);
```

### Alter Table
```sql
ALTER TABLE EMPLOYEE ADD COLUMN department VARCHAR(100);
```

### Drop Table
```sql
DROP TABLE EMPLOYEE;
```

---

## ✍️ DML (Data Manipulation Language)

### Insert Data
```sql
INSERT INTO EMPLOYEE(id, fname, lname, Age, emailID, PhoneNo, City)
VALUES (1, 'Aman', 'Proto', 32, 'aman@gmail.com', '898', 'Delhi');
```

### Update Data
```sql
UPDATE EMPLOYEE
SET Age = 33
WHERE id = 1;
```

### Delete Data
```sql
DELETE FROM EMPLOYEE
WHERE id = 1;
```

---

## 🔍 DQL (Data Query Language)

### Select All Columns
```sql
SELECT * FROM EMPLOYEE;
```

### Select Specific Columns
```sql
SELECT fname, City FROM EMPLOYEE;
```

### WHERE Clause
```sql
SELECT * FROM EMPLOYEE
WHERE City = 'Delhi';
```

---

## 🔗 Joins

### INNER JOIN
```sql
SELECT P.NAME AS ProjectName, E.fname AS Employee
FROM PROJECT P
JOIN EMPLOYEE E ON P.empID = E.id;
```

### LEFT JOIN
```sql
SELECT E.fname, P.NAME
FROM EMPLOYEE E
LEFT JOIN PROJECT P ON E.id = P.empID;
```

### RIGHT JOIN
```sql
SELECT E.fname, P.NAME
FROM EMPLOYEE E
RIGHT JOIN PROJECT P ON E.id = P.empID;
```

### FULL OUTER JOIN (Emulated in MySQL)
```sql
SELECT * FROM EMPLOYEE
LEFT JOIN PROJECT ON EMPLOYEE.id = PROJECT.empID
UNION
SELECT * FROM EMPLOYEE
RIGHT JOIN PROJECT ON EMPLOYEE.id = PROJECT.empID;
```

---

## 📊 Aggregate Functions

### COUNT, SUM, AVG, MIN, MAX
```sql
SELECT COUNT(*) FROM EMPLOYEE;

SELECT AVG(Age) FROM EMPLOYEE;

SELECT MAX(Age), MIN(Age) FROM EMPLOYEE;
```

---

## 🔎 Filtering and Sorting

### LIKE (Pattern Matching)
```sql
SELECT * FROM EMPLOYEE
WHERE fname LIKE 'A%';
```

### ORDER BY
```sql
SELECT * FROM EMPLOYEE
ORDER BY Age DESC;
```

### BETWEEN
```sql
SELECT * FROM EMPLOYEE
WHERE Age BETWEEN 25 AND 40;
```

### IN
```sql
SELECT * FROM EMPLOYEE
WHERE City IN ('Delhi', 'Mumbai');
```

---

## 📚 GROUP BY and HAVING

### GROUP BY
```sql
SELECT City, COUNT(*) AS EmployeeCount
FROM EMPLOYEE
GROUP BY City;
```

### HAVING (used after GROUP BY)
```sql
SELECT City, COUNT(*) AS EmployeeCount
FROM EMPLOYEE
GROUP BY City
HAVING COUNT(*) > 1;
```

---

## 🔁 Subqueries

### Simple Subquery
```sql
SELECT * FROM EMPLOYEE
WHERE Age > (SELECT AVG(Age) FROM EMPLOYEE);
```

---

## 🪟 Views

### Create View
```sql
CREATE VIEW ProjectDetails AS
SELECT P.NAME, E.fname, C.first_name
FROM PROJECT P
JOIN EMPLOYEE E ON P.empID = E.id
JOIN CLIENT C ON P.clientID = C.id;
```

### Select From View
```sql
SELECT * FROM ProjectDetails;
```

---

## ✅ Example Query

### Get All Project Names with Employee and Client Info
```sql
SELECT P.NAME AS ProjectName, E.fname AS Employee, C.first_name AS Client
FROM PROJECT P
JOIN EMPLOYEE E ON P.empID = E.id
JOIN CLIENT C ON P.clientID = C.id;
```

---

## 🧠 Tips

- Use `EXPLAIN` to analyze query performance.
- Always back up data before running `DELETE` or `UPDATE` queries.
- Use constraints (`NOT NULL`, `UNIQUE`, `FOREIGN KEY`) to ensure data integrity.

---

## 👨‍💻 Author

- **Rahul Ghosh**
- 📧 rahulghosh111111@gmail.com

---

## 📜 License

This README is part of an educational MySQL project. Free to use and modify.
