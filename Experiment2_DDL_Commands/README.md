# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**

Create a table named Employees with the following constraints:

EmployeeID should be the primary key.
FirstName and LastName should be NOT NULL.
Email should be unique.
Salary should be greater than 0.
DepartmentID should be a foreign key referencing the Departments table.

```sql
CREATE TABLE Employees(
EmployeeID INTEGER PRIMARY KEY,
FirstName TEXT NOT NULL,
LastName TEXT NOT NULL,
Email TEXT UNIQUE,
Salary INTEGER CHECK(SALARY>0),
DepartmentID INTEGER,
FOREIGN KEY (DepartmentID) REFERENCES Departments(DepartmentID)
);
```

**Output:**

![image](https://github.com/user-attachments/assets/e9f1f6a1-d785-4347-9df9-84359bf2c216)


**Question 2**
---

Create a table named Products with the following constraints:

ProductID should be the primary key.
ProductName should be NOT NULL.
Price is of real datatype and should be greater than 0.
Stock is of integer datatype and should be greater than or equal to 0.


```sql
CREATE TABLE Products(
ProductID INTEGER PRIMARY KEY,
ProductName TEXT NOT NULL,
Price REAL CHECK(Price>0),
Stock INTEGER CHECK(Stock>0)
);
```

**Output:**

![image](https://github.com/user-attachments/assets/26ffd3c7-b5c9-476e-9a35-3b61cb74c7fe)


**Question 3**
---
Write a SQL query to add a column named Date_of_birth as Date in the Student_details table.

```sql
ALTER TABLE Student_details
ADD COLUMN Date_of_birth Date
```

**Output:**
![image](https://github.com/user-attachments/assets/0e30cb33-5edb-4b0e-9e8f-ee7592379db7)

**Question 4**
---
Write an SQL query to add a new column salary of type INTEGER to the Employees table, with a CHECK constraint that ensures the value in this column is greater than 0.

```sql
ALTER TABLE Employees
ADD COLUMN salary INTEGER CHECK(salary>0)
```

**Output:**

![image](https://github.com/user-attachments/assets/db4c16d8-a006-4c86-848d-f30fdb769612)


**Question 5**
---
Insert the following employees into the Employee table:

EmployeeID  Name        Position    Department  Salary
----------  ----------  ----------  ----------  ----------
2           John Smith  Developer   IT          75000
3           Anna Bell   Designer    Marketing   68000

```sql
INSERT INTO Employee(EmployeeID,Name,Position,Department,Salary)VALUES(2,'John Smith','Developer','IT',75000);
INSERT INTO Employee(EmployeeID,Name,Position,Department,Salary)VALUES(3,'Anna Bell','Designer','Marketing',68000
```

**Output:**
![image](https://github.com/user-attachments/assets/ac6715a3-ea4e-4d31-b508-7ced3142a38b)

**Question 6**
---
Create a table named Departments with the following columns:

DepartmentID as INTEGER
DepartmentName as TEXT

```sql
CREATE TABLE Departments(
DepartmentID INTEGER,
DepartmentName TEXT
);
```

**Output:**

![image](https://github.com/user-attachments/assets/6dd06cca-291c-457e-b674-402e052d91bc)


**Question 7**
---
Create a new table named item with the following specifications and constraints:
item_id as TEXT and as primary key.
item_desc as TEXT.
rate as INTEGER.
icom_id as TEXT with a length of 4.
icom_id is a foreign key referencing com_id in the company table.
The foreign key should cascade updates and deletes.
item_desc and rate should not accept NULL.

```sql
CREATE TABLE item(
item_id TEXT PRIMARY KEY,
item_desc TEXT NOT NULL,
rate INTEGER NOT NULL,
icom_id TEXT,
FOREIGN KEY (icom_id) REFERENCES company(com_id)
ON UPDATE CASCADE
ON DELETE CASCADE
CHECK(LENGTH(icom_id)=4)
);
```

**Output:**

![image](https://github.com/user-attachments/assets/e72dcac1-338e-4198-9b67-017eb3b42b1a)


**Question 8**
---
Insert all customers from Old_customers into Customers

Table attributes are CustomerID, Name, Address, Email

```sql
INSERT INTO Customers(CustomerID, Name, Address, Email)
SELECT CustomerID, Name, Address, Email
From Old_customers
```

**Output:**

![image](https://github.com/user-attachments/assets/ffcbdab8-aa68-4ab2-a2ef-83987a1099a8)

**Question 9**
---
Insert the below data into the Books table, allowing the Publisher and Year columns to take their default values.

ISBN             Title                 Author
---------------  --------------------  ---------------
978-6655443321   Big Data Analytics    Karen Adams

Note: The Publisher and Year columns will use their default values.
 
```sql
INSERT INTO Books ('ISBN','TITLE','Author')VALUES('978-6655443321','Big Data Analytics','Karen Adams');
```

**Output:**


![image](https://github.com/user-attachments/assets/f5862001-65c6-40f3-8277-f0f0f08447eb)


**Question 10**
---
Create a table named Attendance with the following constraints:
AttendanceID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
AttendanceDate as DATE.
Status as TEXT should be one of 'Present', 'Absent', 'Leave

```sql
CREATE TABLE Attendance(
AttendanceID INTEGER PRIMARY KEY,
EmployeeID INTEGER, 
AttendanceDate DATE,
Status TEXT CHECK(STATUS IN ('Present','Absent','Leave')),
FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID)

);
```

**Output:**

![image](https://github.com/user-attachments/assets/4fdebff6-87b0-4d78-bf30-62b9ec5b7989)

## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
