# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
--
Update the reorder level to 40 pieces for all products belonging to the 'Grocery' category in the products table.

PRODUCTS TABLE

name               type
-----------------  ---------------
product_id         INT
product_name       VARCHAR(100)
category           VARCHAR(50)
cost_price         DECIMAL(10,2)
sell_price         DECIMAL(10,2)
reorder_lvl        INT
quantity           INT
supplier_id        INT

```sql
UPDATE PRODUCTS
SET reorder_lvl = 40
WHERE category = 'Grocery'
```

**Output:**


![image](https://github.com/user-attachments/assets/d73efb10-44b5-41e9-bac2-f0b43f4d172f)


**Question 2**
---
Write a SQL statement to Increase quantity of all products by 10% to adjust for surplus stock counted

Products table

---------------
product_id
product_name
category
cost_price
sell_price
reorder_lvl
quantity
supplier_id

```sql
UPDATE Products
SET quantity = quantity * 1.10

```

**Output:**


![image](https://github.com/user-attachments/assets/d477be88-c86b-4a3b-8fae-236176091b37)


**Question 3**
---
Write a SQL statement to Increase the selling price by 10% for all products in the 'Bakery' category in the products table.

Products table

---------------
product_id
product_name
category
cost_price
sell_price
reorder_lvl
quantity
supplier_id

```sql
UPDATE Products
SET sell_price = sell_price*1.10
WHERE category = 'Bakery'
```

**Output:**


![image](https://github.com/user-attachments/assets/da43f5cf-bc3a-4cdc-ae00-39b497a95587)


**Question 4**
---
Write a SQL statement to Double the salary for employees in department 20 who have a job_id ending with 'MAN'

Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id

```sql
UPDATE Employees
SET salary = 2*salary
WHERE department_id = 20 AND job_id LIKE '%MAN'
```

**Output:**

![image](https://github.com/user-attachments/assets/e61f0b33-7f07-4ddd-904b-47b221269946)


**Question 5**
---
Write a SQL query to Delete a Specific Surgery whose ID is 3 or surgeon ID is 4.

Sample table: Surgeries

```sql
DELETE FROM Surgeries
WHERE surgery_id = 3 OR surgeon_id = 4
```

**Output:**

![image](https://github.com/user-attachments/assets/27863564-d7d3-40bf-baec-e111f060ae51)


**Question 6**
---
Write a SQL query to Delete customers with 'GRADE' 3 and whose 'CUST_NAME' contains the substring 'BBB', and 'PAYMENT_AMT' is greater than 2000

```sql
DELETE FROM Customer
WHERE GRADE = 3 AND CUST_NAME LIKE '%BBB%' AND PAYMENT_AMT > 2000
```

**Output:**

![image](https://github.com/user-attachments/assets/1b35feaa-dd5e-4f5f-8e70-3544e8a3b64a)


**Question 7**
---
Write a SQL query to Delete customers from 'customer' table where 'CUST_NAME' contains the substring 'Holmes'.

```sql
DELETE FROM Customer
WHERE CUST_NAME LIKE '%Holmes%'
```

**Output:**
![image](https://github.com/user-attachments/assets/79080fcc-86e4-470f-8063-e3f99b883d34)

**Question 8**
---
Write a SQL query to Delete customers from 'customer' table where 'WORKING_AREA' is 'New York'.

```sql
DELETE FROM Customer 
WHERE WORKING_AREA = 'New York'
```

**Output:**

![Output8](output.png)

**Question 9**
---
Write a SQL query to Select all patients who were admitted for one day.
```sql
SELECT patient_id,first_name,admission_date,discharge_date FROM Patients
WHERE admission_date = discharge_date
```

**Output:**


![image](https://github.com/user-attachments/assets/5531202c-bdd1-4583-8c52-6f0d14427cce)


**Question 10**
---
Write a SQL query to classify value2 in the Calculations table as 'Small', 'Medium', or 'Large' based on whether it is less than 10, between 10 and 50, or greater than 50, respectively.

```sql
SELECT id,value2, 
    CASE 
        WHEN value2 < 10 THEN 'Small'
        
        WHEN value2 BETWEEN 10 AND 50 THEN 'Medium'
        
        WHEN value2 > 50 THEN 'Large'
        
        END AS size_category
        
FROM  Calculations
```

**Output:**


![image](https://github.com/user-attachments/assets/2c8b0e89-4ce6-4177-9e90-ea8dc4aaf18b)

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
