
**Understanding DML**

DML commands are used to interact with the **actual data** stored within database tables. They allow you to retrieve (query), add (insert), modify (update), and remove (delete) data records. Unlike DDL, DML operations typically occur within transactions and can be committed (made permanent) or rolled back (undone).

We'll continue using our `CompanyDB` with `Employees` and `Departments` tables as defined in the DDL examples.

**Assumed Table Structures:**

```sql
-- From previous DDL examples:
-- CREATE DATABASE CompanyDB;
-- USE CompanyDB;

CREATE TABLE Departments (
DepartmentID INT PRIMARY KEY,
DepartmentName VARCHAR(100) NOT NULL UNIQUE,
Location VARCHAR(100)
);

CREATE TABLE Employees (
EmployeeID INT PRIMARY KEY,
FirstName VARCHAR(50) NOT NULL,
LastName VARCHAR(50) NOT NULL,
Email VARCHAR(100) UNIQUE,
PhoneNumber VARCHAR(25),
HireDate DATE,
JobTitleID VARCHAR(10), -- Renamed from JobID
Salary DECIMAL(10, 2) CHECK (Salary > 0),
DepartmentID INT,
FOREIGN KEY (DepartmentID) REFERENCES Departments(DepartmentID)
	ON DELETE SET NULL
	ON UPDATE CASCADE
);
```

---

**1. `INSERT` Statement**

Used to add new rows (records) of data into a table.


**A. `INSERT INTO ... VALUES` (Specifying Column Names)**

This is the most explicit and recommended way to insert data, as it clearly maps values to their respective columns. It's robust against changes in table column order.

*   **Syntax:**
```sql
INSERT INTO table_name (column1, column2, column3, ...)
VALUES (value1, value2, value3, ...);
```
*   **Example 1: Inserting a new department**
```sql
INSERT INTO Departments (DepartmentID, DepartmentName, Location)
VALUES (10, 'Human Resources', 'Headquarters - Building A');

INSERT INTO Departments (DepartmentID, DepartmentName, Location)
VALUES (20, 'Sales', 'Downtown Office');

INSERT INTO Departments (DepartmentID, DepartmentName, Location)
VALUES (30, 'IT Support', 'Headquarters - Building B');

INSERT INTO Departments (DepartmentID, DepartmentName) -- Location can be NULL
VALUES (40, 'Marketing');
```
*   **Example 2: Inserting a new employee**
```sql
INSERT INTO Employees (EmployeeID, FirstName, LastName, Email, HireDate, JobTitleID, Salary, DepartmentID)
VALUES (101, 'Alice', 'Smith', 'alice.smith@example.com', '2022-03-15', 'HR_MGR', 75000.00, 10);

INSERT INTO Employees (EmployeeID, FirstName, LastName, Email, PhoneNumber, HireDate, JobTitleID, Salary, DepartmentID)
VALUES (102, 'Bob', 'Johnson', 'bob.j@example.com', '555-1234', '2021-07-01', 'SALE_REP', 60000.00, 20);

-- Inserting an employee without a phone number (PhoneNumber is nullable)
INSERT INTO Employees (EmployeeID, FirstName, LastName, Email, HireDate, JobTitleID, Salary, DepartmentID)
VALUES (103, 'Carol', 'Williams', 'carol.w@example.com', '2023-01-10', 'IT_SPEC', 68000.00, 30);
```
*   **Notes:**
	*   The number of columns listed must match the number of values.
	*   The data types of the values must be compatible with the data types of the corresponding columns.
	*   If a column has a `DEFAULT` constraint and you omit it from the column list, the default value will be used.
	*   If a column is auto-incrementing (e.g., an identity primary key), you typically omit it from the column list, and the database generates the value.

---

**B. `INSERT INTO ... VALUES` (Omitting Column Names)**

Used when you are providing values for *all* columns in the table, and the values are listed in the *exact same order* as the columns appear in the table's definition (as per `DESCRIBE table_name` or `SHOW COLUMNS FROM table_name`).

*   **Syntax:**
```sql
INSERT INTO table_name
VALUES (value1, value2, value3, ...);
```
*   **Example:**
```sql
-- Assuming DepartmentID is not auto-incrementing for Departments
INSERT INTO Departments -- Columns are: DepartmentID, DepartmentName, Location
VALUES (50, 'Finance', 'Headquarters - Building A');

-- Inserting an employee, providing a value for every column in the Employees table's defined order
-- Order: EmployeeID, FirstName, LastName, Email, PhoneNumber, HireDate, JobTitleID, Salary, DepartmentID
INSERT INTO Employees
VALUES (104, 'David', 'Brown', 'david.b@example.com', '555-5678', '2022-09-05', 'FIN_ANL', 72000.00, 50);
```
*   **Caution:**
	*   This method is **less robust**. If the table structure changes (e.g., columns are added, removed, or reordered), this type of `INSERT` statement will likely fail or insert data into the wrong columns.
	*   It's generally **safer and more maintainable to explicitly list the column names.**

---

**C. `INSERT INTO ... SELECT`**

To insert rows into a table based on the result of a `SELECT` query from another table (or the same table).

*   **Syntax:**
```sql
INSERT INTO table_name (column1, column2, ...)
SELECT source_column1, source_column2, ...
FROM source_table
WHERE [condition];
```
*   **Example 1: Archiving old employee records**
```sql
-- First, create an archive table (DDL)
CREATE TABLE Employees_Archive AS
SELECT * FROM Employees WHERE 1=0; -- Creates an empty table with the same structure

-- Now, insert employees hired before a certain date into the archive
INSERT INTO Employees_Archive (EmployeeID, FirstName, LastName, Email, PhoneNumber, HireDate, JobTitleID, Salary, DepartmentID)
SELECT EmployeeID, FirstName, LastName, Email, PhoneNumber, HireDate, JobTitleID, Salary, DepartmentID
FROM Employees
WHERE HireDate < '2022-01-01';
```
*   **Example 2: Populating a summary table**
```sql
-- CREATE TABLE Department_Salaries_Summary (
--     DepartmentID INT PRIMARY KEY,
--     TotalSalary DECIMAL(15,2),
--     AverageSalary DECIMAL(15,2),
--     EmployeeCount INT
-- );

INSERT INTO Department_Salaries_Summary (DepartmentID, TotalSalary, AverageSalary, EmployeeCount)
SELECT
	d.DepartmentID,
	SUM(e.Salary),
	AVG(e.Salary),
	COUNT(e.EmployeeID)
FROM Departments d
JOIN Employees e ON d.DepartmentID = e.DepartmentID
GROUP BY d.DepartmentID;
```
*   **Notes:**
*   The number of columns in the `INSERT` list must match the number of columns in the `SELECT` list.
*   Data types must be compatible.

---

**2. `UPDATE` Statement**

*   **Purpose:** Used to modify existing records (rows) in a table.

---

**A. `UPDATE ... SET ... WHERE`**
*   **Use Case:** To change the values of one or more columns for specific rows that meet a certain condition.
*   **Syntax:**
```sql
UPDATE table_name
SET column1 = value1,
	column2 = value2,
	...
WHERE condition;
```
*   **Example 1: Update an employee's salary and job title**
```sql
UPDATE Employees
SET Salary = 65000.00,
	JobTitleID = 'SALE_SR_REP'
WHERE EmployeeID = 102;
```
*   **Example 2: Give a 5% raise to all employees in the 'IT Support' department**
```sql
UPDATE Employees
SET Salary = Salary * 1.05
WHERE DepartmentID = (SELECT DepartmentID FROM Departments WHERE DepartmentName = 'IT Support');
-- Or if you know DepartmentID for IT Support is 30:
-- WHERE DepartmentID = 30;
```
*   **Example 3: Update an employee's email and phone based on their name**
```sql
UPDATE Employees
SET Email = 'carol.updated@example.com',
	PhoneNumber = '555-9999'
WHERE FirstName = 'Carol' AND LastName = 'Williams';
```
*   **Example 4: Updating a column to NULL**
```sql
UPDATE Departments
SET Location = NULL
WHERE DepartmentName = 'Marketing';
```
*   **Crucial Note on `WHERE` Clause:**
	*   **Always use a `WHERE` clause in your `UPDATE` statements unless you intend to update ALL rows in the table.**
	*   Forgetting the `WHERE` clause is a common and dangerous mistake that can lead to unintended mass data modification.
	*   `UPDATE Employees SET Salary = 0;` -- THIS WOULD SET EVERY EMPLOYEE'S SALARY TO 0!

---

**3. `DELETE` Statement**

*   **Purpose:** Used to remove existing records (rows) from a table.

---

**A. `DELETE FROM ... WHERE`**
*   **Use Case:** To remove specific rows from a table that meet a certain condition.
*   **Syntax:**
```sql
DELETE FROM table_name
WHERE condition;
```
*   **Example 1: Delete an employee by their ID**
```sql
DELETE FROM Employees
WHERE EmployeeID = 104;
```
*   **Example 2: Delete all employees from a specific department (e.g., if the department is being dissolved)**
```sql
-- Assuming 'Old Department' has DepartmentID 99
DELETE FROM Employees
WHERE DepartmentID = 99;
-- Then you might delete the department itself (if no longer referenced or ON DELETE CASCADE is set up)
-- DELETE FROM Departments WHERE DepartmentID = 99;
```
*   **Example 3: Delete employees hired before a certain date who are also in a specific job**
```sql
DELETE FROM Employees
WHERE HireDate < '2020-01-01' AND JobTitleID = 'TEMP_CONT';
```
*   **Crucial Note on `WHERE` Clause:**
*   **Always use a `WHERE` clause in your `DELETE` statements unless you intend to delete ALL rows in the table.**
*   Forgetting the `WHERE` clause is extremely dangerous.
*   `DELETE FROM Employees;` -- THIS WOULD DELETE ALL RECORDS FROM THE Employees TABLE!

---

**B. `DELETE FROM` (Deleting All Rows)**
*   **Use Case:** To remove all rows from a table.
*   **Syntax:**
```sql
DELETE FROM table_name;
```
*   **Example:**
```sql
-- Be very careful with this!
-- DELETE FROM Employees_Archive;
```
*   **Comparison with `TRUNCATE TABLE` (DDL):**
	*   `DELETE FROM table_name;` logs each row deletion, can be rolled back (if not auto-committed), fires `ON DELETE` triggers, and does not reset identity columns.
	*   `TRUNCATE TABLE table_name;` is faster, uses minimal logging, typically doesn't fire triggers, and often resets identity columns. Use `TRUNCATE` when you want to quickly empty a table and don't need row-level logging or trigger execution.

---

**4. `SELECT` Statement (Often considered Data Query Language - DQL, a sub-part of DML)**

*   **Purpose:** Used to retrieve (query) data from one or more tables. This is the most frequently used SQL command.

---

**A. `SELECT specific_columns FROM table_name`**
*   **Use Case:** To retrieve only the specified columns for all rows in a table.
*   **Syntax:**
```sql
SELECT column1, column2, ...
FROM table_name;
```
*   **Example:**
```sql
SELECT FirstName, LastName, Email
FROM Employees;

SELECT DepartmentName, Location
FROM Departments;
```

---

**B. `SELECT * FROM table_name` (Select All Columns)**
*   **Use Case:** To retrieve all columns for all rows in a table.
*   **Syntax:**
```sql
SELECT *
FROM table_name;
```
*   **Example:**
```sql
SELECT * FROM Employees;
SELECT * FROM Departments;
```
*   **Notes:**
	*   Convenient for quick inspection, but generally **not recommended for production application code** because:
		*   It can retrieve unnecessary data, impacting performance.
		*   If the table structure changes (columns added/removed), the application might break if it expects a specific set of columns. Explicitly listing columns is more robust.

---

**C. `SELECT ... WHERE condition` (Filtering Rows)**
*   **Use Case:** To retrieve rows that meet specific criteria.
*   **Syntax:**
```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```
*   **Example 1: Find employees in a specific department**
```sql
SELECT EmployeeID, FirstName, LastName, Salary
FROM Employees
WHERE DepartmentID = 20; -- Sales Department
```
*   **Example 2: Find employees with a salary greater than a certain amount**
```sql
SELECT FirstName, LastName, Salary
FROM Employees
WHERE Salary > 70000;
```
*   **Example 3: Using logical operators (`AND`, `OR`, `NOT`)**
```sql
SELECT EmployeeID, FirstName, LastName, JobTitleID, Salary
FROM Employees
WHERE (DepartmentID = 10 OR DepartmentID = 30) AND Salary < 70000;
```
*   **Example 4: Using comparison operators (`=`, `>`, `<`, `>=`, `<=`, `!=` or `<>`) and `LIKE` for pattern matching**
```sql
SELECT FirstName, LastName, Email
FROM Employees
WHERE LastName LIKE 'S%'; -- Last names starting with 'S'

SELECT EmployeeID, Email
FROM Employees
WHERE Email LIKE '%example.com'; -- Emails ending with 'example.com'
```
*   **Example 5: Checking for `NULL` values**
```sql
SELECT EmployeeID, FirstName, LastName, PhoneNumber
FROM Employees
WHERE PhoneNumber IS NULL;

SELECT DepartmentID, DepartmentName, Location
FROM Departments
WHERE Location IS NOT NULL;
```

---

**D. `SELECT DISTINCT` (Retrieving Unique Values)**
*   **Use Case:** To retrieve only unique (distinct) values for the specified column(s).
*   **Syntax:**
```sql
SELECT DISTINCT column1, column2, ...
FROM table_name;
```
*   **Example 1: Get a list of unique job titles**
```sql
SELECT DISTINCT JobTitleID
FROM Employees;
```
*   **Example 2: Get unique combinations of DepartmentID and JobTitleID**
```sql
SELECT DISTINCT DepartmentID, JobTitleID
FROM Employees;
```

---

**E. `SELECT ... ORDER BY` (Sorting Results)**
*   **Use Case:** To sort the retrieved rows based on one or more columns.
*   **Syntax:**
```sql
SELECT column1, column2, ...
FROM table_name
WHERE [condition]
ORDER BY sort_column1 [ASC|DESC], sort_column2 [ASC|DESC], ...;
```
*   `ASC`: Ascending order (default).
*   `DESC`: Descending order.
*   **Example 1: List employees sorted by last name, then first name**
```sql
SELECT EmployeeID, LastName, FirstName, Salary
FROM Employees
ORDER BY LastName ASC, FirstName ASC;
```
*   **Example 2: List employees by salary in descending order**
```sql
SELECT FirstName, LastName, Salary
FROM Employees
ORDER BY Salary DESC;
```

---

**F. `SELECT ... LIMIT` / `TOP` / `ROWNUM` (Limiting Results)**
*   **Use Case:** To restrict the number of rows returned by a query.
*   **Syntax (varies by DBMS):**
	*   **MySQL, PostgreSQL:** `LIMIT count [OFFSET offset_value]`
	*   **SQL Server:** `SELECT TOP count column1, ...`
	*   **Oracle:** `WHERE ROWNUM <= count` (often used in a subquery for proper ordering)
*   **Example (MySQL/PostgreSQL): Get the top 5 highest-paid employees**
```sql
SELECT EmployeeID, FirstName, LastName, Salary
FROM Employees
ORDER BY Salary DESC
LIMIT 5;
```
*   **Example (MySQL/PostgreSQL): Get employees for pagination (e.g., page 2, 10 items per page)**
```sql
SELECT EmployeeID, FirstName, LastName
FROM Employees
ORDER BY EmployeeID
LIMIT 10 OFFSET 10; -- Skips first 10 rows (page 1), then takes next 10 (page 2)
```

---

**G. `SELECT ... GROUP BY` and Aggregate Functions (`COUNT`, `SUM`, `AVG`, `MAX`, `MIN`)**
*   **Use Case:** To group rows that have the same values in specified columns and perform calculations on each group.
*   **Syntax:**
```sql
SELECT column_to_group_by, aggregate_function(column_to_aggregate)
FROM table_name
WHERE [condition]
GROUP BY column_to_group_by
[HAVING aggregate_condition]; -- Filters groups, similar to WHERE for rows
```
*   **Example 1: Count employees in each department**
```sql
SELECT DepartmentID, COUNT(EmployeeID) AS NumberOfEmployees
FROM Employees
GROUP BY DepartmentID
ORDER BY NumberOfEmployees DESC;
```
*   **Example 2: Calculate average salary for each job title**
```sql
SELECT JobTitleID, AVG(Salary) AS AverageSalary
FROM Employees
GROUP BY JobTitleID;
```
*   **Example 3: Find departments with more than 2 employees**
```sql
SELECT d.DepartmentName, COUNT(e.EmployeeID) AS EmployeeCount
FROM Employees e
JOIN Departments d ON e.DepartmentID = d.DepartmentID
GROUP BY d.DepartmentName
HAVING COUNT(e.EmployeeID) > 2;
```

---

**H. `SELECT ... JOIN` (Combining Data from Multiple Tables)**
*   **Use Case:** To retrieve data by combining rows from two or more tables based on a related column between them.
*   **Types of Joins:** `INNER JOIN`, `LEFT JOIN` (or `LEFT OUTER JOIN`), `RIGHT JOIN` (or `RIGHT OUTER JOIN`), `FULL JOIN` (or `FULL OUTER JOIN`), `CROSS JOIN`.
*   **Syntax (INNER JOIN):**
```sql
SELECT t1.columnA, t2.columnB
FROM table1 t1
INNER JOIN table2 t2 ON t1.common_column = t2.common_column
WHERE [condition];
```
*   **Example 1: Get employee names and their department names (INNER JOIN)**
```sql
SELECT e.FirstName, e.LastName, d.DepartmentName
FROM Employees e
INNER JOIN Departments d ON e.DepartmentID = d.DepartmentID;
```
*   **Example 2: List all departments and any employees in them (LEFT JOIN - shows all departments even if they have no employees)**
```sql
SELECT d.DepartmentName, e.FirstName, e.LastName
FROM Departments d
LEFT JOIN Employees e ON d.DepartmentID = e.DepartmentID
ORDER BY d.DepartmentName, e.LastName;
```

---

**Important Notes for DML Commands:**

*   **Transactions:** DML operations usually happen within a transaction. You use `COMMIT` (TCL command) to make the changes permanent or `ROLLBACK` (TCL command) to undo them. Some tools or DBMS configurations might have an "auto-commit" mode enabled by default for single statements.
*   **`WHERE` Clause:** This is arguably the most critical part of `UPDATE` and `DELETE` statements (and very useful in `SELECT`). Always double-check your `WHERE` conditions to ensure you are affecting only the intended rows.
*   **Performance:** For large tables, DML operations (especially `SELECT` queries without proper indexing, or mass `UPDATE`/`DELETE`) can be slow. Database indexing and query optimization are important.
*   **Data Integrity:** Constraints defined with DDL (like `NOT NULL`, `UNIQUE`, `FOREIGN KEY`, `CHECK`) are enforced during DML operations. If an `INSERT` or `UPDATE` violates a constraint, the operation will typically fail.
