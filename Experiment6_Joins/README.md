# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
--
![image](https://github.com/user-attachments/assets/72a9bd07-2a20-4d84-b253-afaf523ddad8)

```sql
select c.cust_name ,s.name from customer c
left join salesman s on c.salesman_id=s.salesman_id
where c.city=s.city;
```

**Output:**

![image](https://github.com/user-attachments/assets/a4f9bc78-56ec-417f-b2c3-f21cd04f63a5)

**Question 2**
---
![image](https://github.com/user-attachments/assets/289e8296-8feb-4b8d-820e-894143b99077)

```sql

select c.cust_name,c.city,o.ord_no,o.ord_date,o.purch_amt as 'Order Amount',s.name,s.commission
from customer c
left join orders o
on o.customer_id=c.customer_id
left join salesman s
on s.salesman_id=o.salesman_id;
```

**Output:**

![image](https://github.com/user-attachments/assets/00073dee-bcf2-4c1d-991e-a38246790a3d)

**Question 3**
---
![image](https://github.com/user-attachments/assets/d7c6206a-4589-4018-bac6-a42c3179205b)

```sql

select c.cust_name,c.city,c.grade,s.name as Salesman,s.city from customer c
inner join salesman s on c.salesman_id=s.salesman_id
order by c.customer_id asc;
```

**Output:**

![image](https://github.com/user-attachments/assets/9119421e-9d14-4345-856a-6a1d37acb138)

**Question 4**
---
![image](https://github.com/user-attachments/assets/24ed0cf7-c114-4852-9b6d-fccc8a58376e)

```sql
--
select p.* from patients p
inner join test_results t on p.patient_id=t.patient_id
where t.test_name='X-Ray' and t.result='Normal';
```

**Output:**

![image](https://github.com/user-attachments/assets/6faae3a6-8a8d-4853-a193-5f3256069508)

**Question 5**
---
![image](https://github.com/user-attachments/assets/57ac79a2-4d2d-405c-8674-683282dd1855)

```sql
--
SELECT o.ord_no,o.ord_date,o.purch_amt,c.cust_name AS "Customer Name",c.grade,s.name AS "Salesman",s.commission FROM orders o
JOIN 
    customer c ON o.customer_id = c.customer_id
JOIN 
    salesman s ON o.salesman_id = s.salesman_id;
```

**Output:**

![image](https://github.com/user-attachments/assets/9484d9b0-625f-4977-b268-bc521a0442d8)

**Question 6**
---
![image](https://github.com/user-attachments/assets/810e2283-fbc3-43c5-a4a7-bc01a09a3bcc)

```sql
--
select o.ord_no,o.purch_amt,o.ord_date,c.cust_name,c.city as customer_city,
c.grade,s.name as salesman_name,s.city as salesman_city,s.commission from orders o
join customer c on o.customer_id=c.customer_id
join salesman s on o.salesman_id=s.salesman_id;
```

**Output:**

![image](https://github.com/user-attachments/assets/2f8455fc-067f-417a-9a29-7404a1dabeab)

**Question 7**
---
![image](https://github.com/user-attachments/assets/69335516-ffb0-4b0b-a30a-637d452a6f3d)

```sql
--
select p.first_name,s.*
from PATIENTS p
inner join SURGERIES s on p.patient_id = s.patient_id
where p.first_name = 'Alice';
```

**Output:**

![image](https://github.com/user-attachments/assets/06d51edf-733d-49b5-8ea4-17da82d7fe35)

**Question 8**
---
![image](https://github.com/user-attachments/assets/06a8b12b-9a93-40e4-bd5c-3910a9e27f5e)

```sql
--
select p.first_name as patient_name,
d.first_name as doctor_name
from PATIENTS p
inner join DOCTORS d
on p.doctor_id = d.doctor_id
where p.discharge_date is null;
```

**Output:**

![image](https://github.com/user-attachments/assets/5cf1bc6f-dad1-4eff-8224-b848c06913c9)

**Question 9**
---
![image](https://github.com/user-attachments/assets/b9466088-222d-49ac-ab29-715dfb823cdb)

```sql
sql
--
select c.cust_name as "Customer Name",c.city,s.name as Salesman,s.city,s.commission from customer c
join salesman s on c.salesman_id=s.salesman_id
where s.commission>0.12 and c.city<>s.city;
```

**Output:**

![image](https://github.com/user-attachments/assets/c8139797-b38d-40b6-8f9f-20c193aeafaa)

**Question 10**
---
![image](https://github.com/user-attachments/assets/9de321bb-8cb0-46da-93b9-9eb86c7ef9b8)

```sql
--
select c.*
from customer c
left join orders o on o.customer_id = c.customer_id
where o.ord_date > '2012-08-17';
```

**Output:**

![image](https://github.com/user-attachments/assets/1adfc58c-377f-4e39-aed1-36f7422829fb)


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
