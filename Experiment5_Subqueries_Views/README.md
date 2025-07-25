# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
--
-- From the following tables, write a SQL query to determine the commission of the salespeople in Paris. Return commission.

```sql
-- select commission from salesman 
WHERE salesman_id IN (
select salesman_id 
from customer 
where city = 'Paris');
```

**Output:**

![image](https://github.com/user-attachments/assets/46f967fd-06d4-4947-b32e-72c3a1d53566)

**Question 2**
---
-- Write a SQL query that retrieves the names of students and their corresponding grades, where the grade is equal to the maximum grade achieved in each subject.

```sql
-- select student_name, grade 
from GRADES 
WHERE grade = (
select max(grade)
from GRADES as g
where g.subject = GRADES.subject);
```

**Output:**

![image](https://github.com/user-attachments/assets/760d1c41-f03e-4f09-a51a-b32a97a649dc)

**Question 3**
---
-- From the following tables, write a SQL query to find all orders generated by the salespeople who may work for customers whose id is 3007. Return ord_no, purch_amt, ord_date, customer_id, salesman_id.

```sql
-- select ord_no, purch_amt, ord_date, customer_id, salesman_id
from orders 
WHERE salesman_id IN (
select distinct salesman_id 
from orders 
where customer_id = 3007);
```

**Output:**

![image](https://github.com/user-attachments/assets/f2b04d6f-2bda-4108-92f3-f06c7c209624)

**Question 4**
---
-- Write a SQL query to Retrieve the names and cities of customers who have the same city as customers with IDs 3 and 7

```sql
-- select name, city 
from customer 
WHERE city IN (
select city from customer 
where id in (3,7));
```

**Output:**

![image](https://github.com/user-attachments/assets/4239e1e1-a8c2-418b-ae0b-589aafdd7d20)

**Question 5**
---
-- Write a SQL query to Find employees who have an age less than the average age of employees with incomes over 2.5 Lakh
```sql
-- select * from Employee 
WHERE age < (
SELECT AVG(age) from Employee 
WHERE income > 250000);
```

**Output:**

![image](https://github.com/user-attachments/assets/c44c8352-6d5c-4b77-ace2-c96283d467bc)

**Question 6**
---
-- Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose Address as Delhi and age below 30

```sql
SELECT * from CUSTOMERS 
group by ID
HAVING ADDRESS = 'Delhi' and AGE < 30;
```

**Output:**

![image](https://github.com/user-attachments/assets/5e27049d-b9d3-4025-a4d8-c5fabc92962f)

**Question 7**
---
-- Write a SQL query to Retrieve the medications with dosages equal to the lowest dosage

Table Name: Medications (attributes: medication_id, medication_name, dosage)

```sql
-- SELECT medication_id as medic, medication_name, dosage 
from Medications 
WHERE dosage = (
Select min(dosage) 
from Medications);
```

**Output:**

![image](https://github.com/user-attachments/assets/e22ef6b5-a041-4ceb-9ab8-a3ba7cb1e652)

**Question 8**
---
-- Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose AGE is LESS than $30
```sql
-- SELECT * from CUSTOMERS 
WHERE AGE < 30;
```

**Output:**

![image](https://github.com/user-attachments/assets/bc98624f-bb3c-4906-ba54-9966539b9a96)

**Question 9**
---
-- From the following tables write a SQL query to find all orders generated by London-based salespeople. Return ord_no, purch_amt, ord_date, customer_id, salesman_id.

```sql
-- select * from orders 
WHERE salesman_id IN (
select salesman_id 
from salesman 
WHERE city = 'London');
```

**Output:**

![image](https://github.com/user-attachments/assets/dd8522d8-2c41-426a-b0b0-d7e90adb81f7)

**Question 10**
---
-- From the following tables, write a SQL query to find all the orders issued by the salesman 'Paul Adam'. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.

```sql
-- SELECT * from orders 
WHERE salesman_id = (
SELECT salesman_id 
FROM salesman 
WHERE name = 'Paul Adam');
```

**Output:**

![image](https://github.com/user-attachments/assets/da2cd360-33f6-4612-82d1-03d0a2c7cb07)


## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
