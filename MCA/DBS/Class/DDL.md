
Understanding DDL

DDL commands are used to define, modify, and manage the structure of database objects like tables, indexes, views, etc. They manipulate the metadata (data about data) rather than the actual data records themselves. Changes made by DDL commands are generally auto-committed (they don't need a separate `COMMIT` statement) and can be significant, so they should be used with care.


**1. `CREATE` Command**

*   **Purpose:** Used to build new database objects from scratch.

---

**A. `CREATE DATABASE`**
*   **Use Case:** To create a new, empty logical container for all other database objects (tables, views, etc.).
*   **Syntax:**
```sql
CREATE DATABASE database_name;
```
*   **Example:**
```sql
CREATE DATABASE CompanyDB;
```
*   **Notes:**
*   The exact syntax and options can vary slightly between DBMS (e.g., MySQL, PostgreSQL, SQL Server, Oracle).
*   In many systems, database creation is handled via administrative tools or specific commands outside of a standard SQL session connected to an existing database.
*   You usually need special privileges to create a database.

---

**B. `CREATE TABLE`**
*   **Use Case 1: Basic Table Creation**
*   Defining columns and their data types.
*   **Syntax:**
```sql
CREATE TABLE table_name (
	column1_name datatype [constraints],
	column2_name datatype [constraints],
	...
	[table_level_constraints]
);
```
*   **Example:**
```sql
-- First, ensure you are using the correct database (DBMS-specific command)
-- USE CompanyDB; -- Example for MySQL or SQL Server

CREATE TABLE Departments (
	DepartmentID INT PRIMARY KEY,  -- Inline constraint for primary key
	DepartmentName VARCHAR(100) NOT NULL UNIQUE,
	Location VARCHAR(100)
);

CREATE TABLE Employees (
	EmployeeID INT,
	FirstName VARCHAR(50) NOT NULL,
	LastName VARCHAR(50) NOT NULL,
	Email VARCHAR(100) UNIQUE,
	PhoneNumber VARCHAR(20),
	HireDate DATE,
	JobID VARCHAR(10),
	Salary DECIMAL(10, 2) CHECK (Salary > 0), -- Inline CHECK constraint
	DepartmentID INT,
	PRIMARY KEY (EmployeeID), -- Table-level constraint
	FOREIGN KEY (DepartmentID) REFERENCES Departments(DepartmentID) -- Table-level constraint
	ON DELETE SET NULL  -- Optional: what to do if a referenced department is deleted
	ON UPDATE CASCADE   -- Optional: what to do if a referenced DepartmentID changes
);
```
*   **Common Column Constraints:**
*   `NOT NULL`: Ensures a column cannot have a NULL value.
*   `UNIQUE`: Ensures all values in a column (or set of columns) are different.
*   `PRIMARY KEY`: A combination of `NOT NULL` and `UNIQUE`. Uniquely identifies each record in a table.
*   `FOREIGN KEY`: Links a column (or set of columns) in one table to a `PRIMARY KEY` or `UNIQUE` key in another table, enforcing referential integrity.
*   `CHECK`: Ensures that all values in a column satisfy a specific condition.
*   `DEFAULT`: Sets a default value for a column when no value is specified during `INSERT`.

*   **Use Case 2: Create Table As Select (CTAS)**
*   Creating a new table based on the structure and/or data of an existing table or a query result.
*   **Syntax:**
```sql
CREATE TABLE new_table_name AS
SELECT column1, column2, ...
FROM existing_table_name
WHERE [condition];
```
*   **Example 1: Copying structure and all data**
```sql
CREATE TABLE Employees_Backup AS
SELECT * FROM Employees;
```
*   **Example 2: Copying structure and specific data**
```sql
CREATE TABLE HighEarner_Employees AS
SELECT EmployeeID, FirstName, LastName, Salary
FROM Employees
WHERE Salary > 70000;
```
*   **Example 3: Copying only structure (no data)**
```sql
CREATE TABLE Employees_Template AS
SELECT * FROM Employees WHERE 1=0; -- Condition that is always false
```
*   **Notes for CTAS:**
*   Column data types in the new table are inferred from the `SELECT` statement.
*   Constraints (like `PRIMARY KEY`, `FOREIGN KEY`, `NOT NULL`) are often *not* copied automatically by CTAS. You might need to add them later using `ALTER TABLE`. This behavior can vary by DBMS.

---

**C. `CREATE INDEX`**
*   **Use Case:** To improve the speed of data retrieval operations on a table. Indexes can also be used to enforce uniqueness.
*   **Syntax:**
```sql
CREATE [UNIQUE] INDEX index_name
ON table_name (column1_name [ASC|DESC], column2_name [ASC|DESC], ...);
```
*   **Example 1: Single-column index**
```sql
CREATE INDEX idx_emp_lastname
ON Employees (LastName);
```
*   **Example 2: Composite (multi-column) index**
```sql
CREATE INDEX idx_emp_dept_job
ON Employees (DepartmentID, JobID);
```
*   **Example 3: Unique index (prevents duplicate values)**
```sql
-- Note: We already made Email UNIQUE in CREATE TABLE, but this is how you'd add it later
-- or if it wasn't specified initially.
CREATE UNIQUE INDEX idx_emp_email_unique
ON Employees (Email);
```
*   **Notes:**
*   Primary keys automatically get an index.
*   While indexes speed up queries, they can slow down data modification operations (`INSERT`, `UPDATE`, `DELETE`) because the index also needs to be updated.

---

**D. `CREATE VIEW`**
*   **Use Case:** To create a virtual table based on the result-set of a stored SQL query. Views can simplify complex queries, provide a layer of security by restricting access to underlying table columns, or present data in a specific format.
*   **Syntax:**
```sql
CREATE [OR REPLACE] VIEW view_name AS
SELECT column1, column2, ...
FROM table_name
WHERE [condition]
[WITH CHECK OPTION]; -- Optional: Enforces that DML on the view adheres to its WHERE clause
```
*   **Example 1: Simple view to show only specific employee details**
```sql
CREATE VIEW Employee_ContactInfo AS
SELECT EmployeeID, FirstName, LastName, Email, PhoneNumber
FROM Employees;
```
*   *Usage:* `SELECT * FROM Employee_ContactInfo WHERE LastName = 'Smith';`

*   **Example 2: View with a join**
```sql
CREATE VIEW Employee_Department_Details AS
SELECT e.EmployeeID, e.FirstName, e.LastName, d.DepartmentName, d.Location
FROM Employees e
JOIN Departments d ON e.DepartmentID = d.DepartmentID;
```
*   *Usage:* `SELECT * FROM Employee_Department_Details WHERE DepartmentName = 'Sales';`

---

**E. `CREATE PROCEDURE` / `CREATE FUNCTION`**
*   **Use Case:** To create stored procedures or functions (blocks of SQL code) that can be saved in the database and executed later. This is a broader topic, but their creation is a DDL operation.
*   **Syntax (varies significantly by DBMS):**
```sql
-- Example for a simple procedure (syntax is highly DBMS-specific)
-- For SQL Server:
-- CREATE PROCEDURE GetEmployeeById (@EmpID INT)
-- AS
-- BEGIN
--     SELECT * FROM Employees WHERE EmployeeID = @EmpID;
-- END;

-- For PostgreSQL:
-- CREATE OR REPLACE FUNCTION GetEmployeeFullName(emp_id INT)
-- RETURNS VARCHAR AS $$
-- DECLARE
--    full_name VARCHAR;
-- BEGIN
--    SELECT FirstName || ' ' || LastName INTO full_name FROM Employees WHERE EmployeeID = emp_id;
--    RETURN full_name;
-- END;
-- $$ LANGUAGE plpgsql;
```
*   **Notes:** Stored procedures and functions are DDL because they define a new database object.

---

**2. `ALTER` Command**

*   **Purpose:** Used to modify the structure of existing database objects. Most commonly used with tables.

---

**A. `ALTER TABLE ... ADD COLUMN`**
*   **Use Case:** To add a new column to an existing table.
*   **Syntax:**
```sql
ALTER TABLE table_name
ADD COLUMN column_name datatype [constraints];
```
*   **Example 1: Adding a simple column**
```sql
ALTER TABLE Employees
ADD COLUMN MiddleName VARCHAR(50);
```
*   **Example 2: Adding a column with a default value and NOT NULL (important for tables with existing data)**
```sql
ALTER TABLE Employees
ADD COLUMN IsActive BOOLEAN DEFAULT TRUE NOT NULL;
```

---

**B. `ALTER TABLE ... DROP COLUMN`**
*   **Use Case:** To remove an existing column from a table.
*   **Syntax:**
```sql
ALTER TABLE table_name
DROP COLUMN column_name;
```
*   **Example:**
```sql
ALTER TABLE Employees
DROP COLUMN MiddleName;
```
*   **Note:** Dropping a column permanently deletes the column and all its data.

---

**C. `ALTER TABLE ... MODIFY COLUMN` / `ALTER COLUMN`**
*   **Use Case:** To change the data type, size, or constraints of an existing column.
*   **Syntax (varies by DBMS):**
*   **Oracle, MySQL:**
```sql
ALTER TABLE table_name
MODIFY COLUMN column_name new_datatype [new_constraints];
```
*   **SQL Server, PostgreSQL:**
```sql
ALTER TABLE table_name
ALTER COLUMN column_name TYPE new_datatype; -- For data type

ALTER TABLE table_name
ALTER COLUMN column_name SET NOT NULL; -- To add NOT NULL

ALTER TABLE table_name
ALTER COLUMN column_name DROP NOT NULL; -- To remove NOT NULL
```
*   **Example 1: Change data type (MySQL/Oracle syntax)**
```sql
ALTER TABLE Employees
MODIFY COLUMN PhoneNumber VARCHAR(25);
```
*   **Example 2: Change data type (PostgreSQL/SQL Server syntax)**
```sql
ALTER TABLE Employees
ALTER COLUMN PhoneNumber TYPE VARCHAR(25);
```
*   **Example 3: Add a NOT NULL constraint (MySQL/Oracle syntax)**
```sql
ALTER TABLE Employees
MODIFY COLUMN HireDate DATE NOT NULL;
```
*   **Example 4: Add a default value (SQL Server)**
```sql
ALTER TABLE Employees
ADD CONSTRAINT DF_HireDate DEFAULT GETDATE() FOR HireDate;
-- First drop if it exists and if HireDate was nullable and you want to make it NOT NULL:
-- UPDATE Employees SET HireDate = GETDATE() WHERE HireDate IS NULL;
-- ALTER TABLE Employees ALTER COLUMN HireDate DATE NOT NULL;
```
*   **Note:** Modifying a column's data type can lead to data loss or errors if existing data is incompatible with the new type.

---

**D. `ALTER TABLE ... ADD CONSTRAINT`**
*   **Use Case:** To add a constraint (like `PRIMARY KEY`, `FOREIGN KEY`, `UNIQUE`, `CHECK`) to an existing table.
*   **Syntax:**
```sql
ALTER TABLE table_name
ADD CONSTRAINT constraint_name constraint_definition;
```
*   **Example 1: Adding a UNIQUE constraint**
```sql
ALTER TABLE Employees
ADD CONSTRAINT uq_emp_phonenumber UNIQUE (PhoneNumber);
```
*   **Example 2: Adding a FOREIGN KEY constraint**
```sql
-- Assuming DepartmentID column exists but FK was not defined initially
ALTER TABLE Employees
ADD CONSTRAINT fk_emp_dept
FOREIGN KEY (DepartmentID) REFERENCES Departments(DepartmentID);
```

---

**E. `ALTER TABLE ... DROP CONSTRAINT`**
*   **Use Case:** To remove an existing constraint from a table.
*   **Syntax:**
```sql
ALTER TABLE table_name
DROP CONSTRAINT constraint_name;
-- For MySQL, if it's a primary key:
-- ALTER TABLE table_name DROP PRIMARY KEY;
-- For MySQL, if it's a foreign key:
-- ALTER TABLE table_name DROP FOREIGN KEY constraint_name; (constraint_name is often auto-generated if not specified)
```
*   **Example:**
```sql
ALTER TABLE Employees
DROP CONSTRAINT uq_emp_phonenumber;
```

---

**F. `ALTER TABLE ... RENAME COLUMN`**
*   **Use Case:** To change the name of an existing column.
*   **Syntax (varies by DBMS):**
*   **MySQL, Oracle, PostgreSQL:**
```sql
ALTER TABLE table_name
RENAME COLUMN old_column_name TO new_column_name;
```
*   **SQL Server:**
```sql
EXEC sp_rename 'table_name.old_column_name', 'new_column_name', 'COLUMN';
```
*   **Example (MySQL/Oracle/PostgreSQL):**
```sql
ALTER TABLE Employees
RENAME COLUMN JobID TO JobTitleID;
```

---

**3. `DROP` Command**

*   **Purpose:** Used to permanently delete existing database objects. This action is irreversible without a backup.

---

**A. `DROP TABLE`**
*   **Use Case:** To delete a table and all its data, indexes, triggers, and constraints.
*   **Syntax:**
```sql
DROP TABLE table_name [CASCADE CONSTRAINTS | RESTRICT]; -- Options vary
```
*   **Example:**
```sql
DROP TABLE Employees_Backup;
```
*   **Notes:**
*   `CASCADE CONSTRAINTS` (Oracle) or similar options in other DBMS might be needed if other tables have foreign keys referencing the table being dropped.
*   `RESTRICT` (default in some systems) prevents dropping if other objects depend on it.

---

**B. `DROP INDEX`**
*   **Use Case:** To delete an existing index.
*   **Syntax (varies slightly):**
*   **Most DBMS:**
```sql
DROP INDEX index_name ON table_name;
```
*   **MySQL:**
```sql
ALTER TABLE table_name DROP INDEX index_name;
-- OR
DROP INDEX index_name ON table_name;
```
*   **Example (General):**
```sql
DROP INDEX idx_emp_lastname ON Employees;
```

---

**C. `DROP VIEW`**
*   **Use Case:** To delete an existing view.
*   **Syntax:**
```sql
DROP VIEW view_name;
```
*   **Example:**
```sql
DROP VIEW Employee_ContactInfo;
```

---

**D. `DROP DATABASE`**
*   **Use Case:** To delete an entire database and all objects within it.
*   **Syntax:**
```sql
DROP DATABASE database_name;
```
*   **Example:**
```sql
-- Be extremely careful with this command!
-- DROP DATABASE CompanyDB_Test;
```
*   **Note:** This is a very destructive operation. Ensure you have backups and are certain.

---

**4. `TRUNCATE` Command**

*   **Purpose:** Used to remove all rows of data from a table quickly and efficiently.
*   **Syntax:**
```sql
TRUNCATE TABLE table_name;
```
*   **Example:**
```sql
-- Assuming Employees_Temp is a table we want to clear for new data loading
TRUNCATE TABLE Employees_Temp;
```
*   **Key Differences from `DELETE FROM table_name;` (DML):**
*   **Speed:** `TRUNCATE` is generally much faster for deleting all rows because it deallocates data pages rather than deleting rows individually.
*   **Logging:** `TRUNCATE` typically uses minimal transaction logging, making it harder (or impossible without full backups) to recover the deleted data. `DELETE` logs each row deletion.
*   **Triggers:** `TRUNCATE` usually does not fire `ON DELETE` triggers. `DELETE` does.
*   **Identity Reset:** `TRUNCATE` often resets identity columns (auto-incrementing primary keys) back to their seed value. `DELETE` does not.
*   **WHERE clause:** `TRUNCATE` cannot have a `WHERE` clause; it always removes all rows. `DELETE` can use a `WHERE` clause to remove specific rows.
*   **DDL vs. DML:** `TRUNCATE` is a DDL command. `DELETE` is a DML command.

---

**5. `RENAME` Command**

*   **Purpose:** Used to change the name of an existing database object.

---

**A. `RENAME TABLE`**
*   **Use Case:** To change the name of an existing table.
*   **Syntax (varies by DBMS):**
*   **Most common (e.g., MySQL prior to 8.0, PostgreSQL, Oracle):**
```sql
ALTER TABLE old_table_name
RENAME TO new_table_name;
```
*   **MySQL 8.0+ and some others:**
```sql
RENAME TABLE old_table_name TO new_table_name;
```
*   **SQL Server:**
```sql
EXEC sp_rename 'old_table_name', 'new_table_name';
```
*   **Example (using `ALTER TABLE` syntax):**
```sql
ALTER TABLE Employees
RENAME TO Staff_Members;
```
*   **Example (using `RENAME TABLE` syntax):**
```sql
RENAME TABLE Staff_Members TO Employees;
```

---

**B. `RENAME DATABASE`**
*   **Use Case:** To change the name of an entire database.
*   **Syntax:** Highly DBMS-specific and often not a direct SQL command executed within a standard session.
*   **MySQL:** Requires specific steps, often involving dumping, creating a new database, and importing. No simple `RENAME DATABASE` SQL command.
*   **SQL Server:**
```sql
ALTER DATABASE old_database_name MODIFY NAME = new_database_name;
```
*   **PostgreSQL:**
```sql
ALTER DATABASE old_database_name RENAME TO new_database_name;
```
*   **Note:** This operation can be complex and may require exclusive access to the database.

---

**6. `COMMENT` Command**

*   **Purpose:** Used to add descriptive comments or metadata to database objects (like tables or columns) within the database's data dictionary. This is for documentation purposes.
*   **Note:** This is different from SQL script comments (`--` for single line, `/* ... */` for multi-line) which are ignored by the database engine. `COMMENT ON` stores the comment *in the database*.

---

**A. `COMMENT ON TABLE`**
*   **Use Case:** To add a description to a table.
*   **Syntax:**
```sql
COMMENT ON TABLE table_name IS 'Your descriptive comment here.';
```
*   **Example:**
```sql
COMMENT ON TABLE Employees IS 'Stores information about all company employees.';
```

---

**B. `COMMENT ON COLUMN`**
*   **Use Case:** To add a description to a specific column in a table.
*   **Syntax:**
```sql
COMMENT ON COLUMN table_name.column_name IS 'Your descriptive comment here.';
```
*   **Example:**
```sql
COMMENT ON COLUMN Employees.EmployeeID IS 'Unique identifier for each employee. Primary Key.';
COMMENT ON COLUMN Employees.HireDate IS 'The date when the employee was officially hired.';
```

---

**General Important Notes for DDL Commands:**

*   **DBMS Variations:** While the core concepts are similar, the exact syntax and available options for DDL commands can vary significantly between different Database Management Systems (e.g., MySQL, PostgreSQL, SQL Server, Oracle, SQLite). Always refer to the specific documentation for your DBMS.
*   **Permissions:** Executing DDL commands usually requires higher privileges than DML commands.
*   **Impact:** DDL operations modify the database structure and are often irreversible without backups. Plan carefully.
*   **Auto-Commit:** Most DDL statements are implicitly committed; they take effect immediately and cannot be rolled back as part of a user-defined transaction in the same way DML statements can.
*   **Locking:** DDL operations can sometimes require exclusive locks on database objects, potentially impacting concurrent users.

