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
-- Write an SQL query to change the name of the column id to employee_id in the table employee

```
-- ALTER TABLE employee
RENAME COLUMN id TO
employee_id;
```

**Output:**

![image](https://github.com/user-attachments/assets/ac9f075c-04a6-443d-9a07-13c5de172188)

**Question 2**
---
--In the Employee table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

EmployeeID Name Position Department Salary
5 George Clark Consultant 7 Noah Davis Manager HR 60000 8 Ava Miller Consultant IT

```sql
-- INSERT INTO Employee (EmployeeID,Name,Position,Department,Salary)
VALUES (5,'George Clark','Consultant',NULL,NULL);
INSERT INTO Employee (EmployeeID,Name,Position,Department,Salary)
VALUES(7,'Noah Davis','Manager','HR',60000);
INSERT INTO Employee (EmployeeID,Name,Position,Department,Salary)
VALUES(8,'Ava Miller','Consultant','IT',NULL);

```

**Output:**

![image](https://github.com/user-attachments/assets/b9504cd8-8e21-4e83-b9f0-eb1df4f3fcdc)

**Question 3**
---
-- Create a new table named item with the following specifications and constraints: item_id as TEXT and as primary key. item_desc as TEXT. rate as INTEGER. icom_id as TEXT with a length of 4. icom_id is a foreign key referencing com_id in the company table. The foreign key should cascade updates and deletes. item_desc and rate should not accept NULL.

```sql
-- CREATE TABLE item(
    item_id text primary key,
    item_desc text not null,
    rate integer not null,
    icom_id text(4),
    foreign key (icom_id)references company(com_id)
    on update cascade
    on delete cascade
);
```

**Output:**

![image](https://github.com/user-attachments/assets/9417072e-c9e0-4319-829b-e7affc4abd1f)

**Question 4**
---
-- nsert the below data into the Customers table, allowing the City and ZipCode columns to take their default values.

CustomerID Name Address
304 Peter Parker Spider St

Note: The City and ZipCode columns will use their default values.
```sql
-- insert into Customers(CustomerID,Name,Address)
values(304,'Peter Parker','Spider St');
```

**Output:**

![image](https://github.com/user-attachments/assets/cbf4e69c-a8b3-4f01-ad6e-9a74b03776ca)

**Question 5**
---
--  Insert all employees from Former_employees into Employee

Table attributes are EmployeeID, Name, Department, Salary

```sql
-- insert into Employee(EmployeeID, Name, Department, Salary)
select EmployeeID, Name, Department, Salary from Former_employees;
```

**Output:**

![image](https://github.com/user-attachments/assets/c9a6e5bb-a8c7-486f-8d07-fee803f16b60)

**Question 6**
---
-- Create a table named Invoices with the following constraints:

InvoiceID as INTEGER should be the primary key. InvoiceDate as DATE. DueDate as DATE should be greater than the InvoiceDate. Amount as REAL should be greater than 0.

```sql
-- create table Invoices(
    InvoiceID INTEGER primary key,
    InvoiceDate DATE ,
    DueDate DATE  CHECK(DueDate>InvoiceDate),
    Amount real  check (Amount>0)
);
```

**Output:**

![image](https://github.com/user-attachments/assets/aa363294-122b-4643-a7ac-da04dab48e92)

**Question 7**
---
-- Write a SQL query to Add a new column Mobilenumber as number in the Student_details table.

Sample table: Student_details

cid name type notnu dflt_value pk
0 RollNo int 0 1 1 Name VARCHAR(100) 1 0 2 Gender TEXT 1 0 3 Subject VARCHAR(30) 0 0 4 MARKS INT (3) 0 0
```sql
-- alter table Student_details
add column Mobilenumber number;
```

**Output:**

![image](https://github.com/user-attachments/assets/0db86e9c-c9f4-45f5-ae75-6ba93360df7f)

**Question 8**
---
-- Create a table named Products with the following constraints: ProductID as INTEGER should be the primary key. ProductName as TEXT should be unique and not NULL. Price as REAL should be greater than 0. StockQuantity as INTEGER should be non-negative.

```sql
-- create table Products(
    ProductID integer primary key ,
    ProductName text not null UNIQUE,
    Price real check (Price>0),
    StockQuantity integer check (StockQuantity>0)
);
```

**Output:**

![image](https://github.com/user-attachments/assets/321ace7f-168a-4f2f-8298-9eb266dbedf7)

**Question 9**
---
-- Create a table named Products with the following columns:

ProductID as INTEGER ProductName as TEXT Price as REAL Stock as INTEGER
```sql
-- create table Products(
    ProductID INTEGER,
    ProductName TEXT,
    Price REAL,
    Stock INTEGER
);
```

**Output:**

![image](https://github.com/user-attachments/assets/27bce2b0-1315-4c27-9ecf-513dace671f5)

**Question 10**
---
-- Create a table named ProjectAssignments with the following constraints: AssignmentID as INTEGER should be the primary key. EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID). ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID). AssignmentDate as DATE should be NOT NULL.

```sql
-- create table ProjectAssignments(
    AssignmentID INTEGER primary key,
    EmployeeID INTEGER,
    ProjectID INTEGER,
    AssignmentDate DATE NOT NULL,
    foreign key(EmployeeID) references Employees(EmployeeID)
    foreign key(projectID) references Projects(ProjectID)
    
);
```

**Output:**

![image](https://github.com/user-attachments/assets/3ffedbee-0f87-4091-bc74-cd2451a34ffb)


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
