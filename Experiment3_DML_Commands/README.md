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
-- Update the reorder level to 40 pieces for all products belonging to the 'Grocery' category in the products table.

```sql
-- UPDATE products
SET reorder_lvl = 40
WHERE category = 'Grocery'
```

**Output:**

![image](https://github.com/user-attachments/assets/4b022851-586a-46cd-925d-b22762c5a762)

**Question 2**
---
-- Write a SQL statement to change the email column of employees table with 'Unavailable' for all employees in employees table.

```sql
-- UPDATE Employees
SET email = 'Unavailable';
```

**Output:**

![image](https://github.com/user-attachments/assets/a802e32b-3043-4b87-b5ce-14529c2e4eb0)

**Question 3**
---
-- Write a SQL statement to Increase the salary by 500 and email as 'updated' for employees with job ID 'SA_REP' and commission percentage greater than 0.15

```sql
-- UPDATE Employees
SET salary = salary + 500, email = 'updated'
WHERE job_id = 'SA_REP' AND commission_pct > 0.15; ```

**Output:**

![image](https://github.com/user-attachments/assets/97ba6000-5ae6-428a-98ac-f4482c2df580)

**Question 4**
---
-- Write a SQL statement to Update the reorder level to 20 where the quantity in stock is less than 10 and product category is 'Snacks' in the products table.

```sql
-- UPDATE products
SET reorder_lvl = 20
WHERE  quantity < 10 and category = 'Snacks';
```

**Output:**

![image](https://github.com/user-attachments/assets/12dbcaa0-b6da-4f69-b927-758ee3651985)

**Question 5**
---
--Write a SQL statement to Increase quantity of all products by 10% to adjust for surplus stock counted

```sql
-- UPDATE Products
SET quantity = quantity * 1.1;
```

**Output:**

![image](https://github.com/user-attachments/assets/93464f93-5895-4c8c-a9c7-a57ccaa79261)

**Question 6**
---
--Write a SQL query to Delete customers from 'customer' table where 'GRADE' is odd. 

```sql
-- DELETE FROM customer
WHERE GRADE % 2 != 0;
```

**Output:**

![image](https://github.com/user-attachments/assets/c5802ba1-b1ce-49fc-978c-814ad208d063)

**Question 7**
---
-- Write a SQL query to Delete customers from 'customer' table where 'CUST_CITY' is not 'New York' and 'OUTSTANDING_AMT' is greater than 5000.

```sql
-- DELETE FROM customer
WHERE CUST_CITY != 'New York' and OUTSTANDING_AMT > 5000;
```

**Output:**

![image](https://github.com/user-attachments/assets/c97aceb6-bbe7-4a74-8eb6-ff0146100841)

**Question 8**
---
-- Write a SQL query to Delete All Doctors whose ID ranges from 2 to 4.

```sql
-- DELETE FROM doctors
WHERE doctor_id BETWEEN 2 AND 4;
```

**Output:**

![image](https://github.com/user-attachments/assets/f0b64463-57ab-4990-b1cb-4eab5d202689)

**Question 9**
---
--Write a SQL query to Delete a Specific Surgery whose ID is 3

```sql
-- DELETE FROM surgeries
WHERE surgery_id = 3;
```

**Output:**

![image](https://github.com/user-attachments/assets/17869a04-4926-4ed1-b32f-01b8675ade89)

**Question 10**
---
--  Write a SQL query to remove rows from the table 'customer' with the following condition

```sql
-- DELETE FROM customer 
WHERE CUST_CITY LIKE 'L%';
```

**Output:**

![image](https://github.com/user-attachments/assets/2e332fb2-293c-4ece-8989-4d7b55cd6b88)

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
