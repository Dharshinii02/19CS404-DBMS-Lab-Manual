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
-- Write a SQL statement to Increase the selling price by 15% in the products table where quantity in stock is less than 50 and supplier ID is 10.

Products Table 

name          type       
----------    ---------- 
product_id     INT PRIMARY KEY        
product_name   VARCHAR(10) 
category       VARCHAR(50) 
cost_price     DECIMAL(10) 
sell_price     DECIMAL(10) 
reorder_lv     INT        
quantity       INT        
supplier_id    INT     

```sql
update Products
set sell_price=sell_price *1.15
where quantity < 50
  and supplier_id=10;
```

**Output:**

<img width="1208" height="476" alt="Screenshot 2025-10-15 103033" src="https://github.com/user-attachments/assets/1417a020-59e7-4afc-ac1c-04f365ad7a24" />


**Question 2**
---
Write a SQL query to reduce the reorder level by 30% where cost price is more than 50 and quantity in stock is less than 100 in the products table.

Products Table 

name          type       
----------    ---------- 
product_id     INT PRIMARY KEY        
product_name   VARCHAR(10) 
category       VARCHAR(50) 
cost_price     DECIMAL(10) 
sell_price     DECIMAL(10) 
reorder_lvl    INT        
quantity       INT        
supplier_id    INT               

```sql
update Products
set reorder_lvl = reorder_lvl *0.7
where cost_price > 50
  and quantity < 100;
```

**Output:**

<img width="1217" height="439" alt="Screenshot 2025-10-15 103047" src="https://github.com/user-attachments/assets/54cf7769-f923-4022-9994-d7af12f31a77" />


**Question 3**
---
Write a SQL statement to change the first_name column of employees table with 'John' for those employees whose department_id is 80 and gets a commission_pct below 0.35.

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
update employees
set first_name = 'John'
where department_id = 80
  and commission_pct < 0.35;
```

**Output:**

<img width="1204" height="530" alt="Screenshot 2025-10-15 103101" src="https://github.com/user-attachments/assets/e64e4c1f-32bf-4115-bbf0-46708f891b5c" />

**Question 4**
---
Write a SQL statement to Update the address to '58 Lakeview, Magnolia' where supplier ID is 5 in the suppliers table.

Suppliers Table 

name               type
-----------------  ---------------
supplier_id        INT
supplier_name      VARCHAR(100)
contact_person     VARCHAR(100)
phone_number       VARCHAR(20)
email              VARCHAR(100)
address            VARCHAR(250)

```sql
update suppliers
set address = '58 Lakeview, Magnolia'
where supplier_id=5;
```

**Output:**

<img width="1209" height="404" alt="Screenshot 2025-10-15 103110" src="https://github.com/user-attachments/assets/cb3a317e-9054-4b62-a8a0-ab062608bfba" />


**Question 5**
---
Write a SQL query to find customers who are from the city 'London' who have a grade greater than 200. Return customer_id, cust_name, city, grade, and salesman_id.

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002

```sql
select customer_id, cust_name, city, grade, salesman_id
from customer
where city = 'London'
   And grade > 200;
```

**Output:**

<img width="1216" height="353" alt="Screenshot 2025-10-15 102835" src="https://github.com/user-attachments/assets/9792fab1-fa2a-4b52-87f5-54c11c8265bf" />


**Question 6**
---
Write a SQL query to Delete a Specific Surgery which was made on 28th Feb 2024.

Sample table: Surgeries

attributes: surgery_id, patient_id, surgeon_id, surgery_date
For example:

```sql
delete from surgeries
where surgery_date = '2024-02-28';
```

**Output:**

<img width="1205" height="377" alt="Screenshot 2025-10-15 103321" src="https://github.com/user-attachments/assets/ac706d35-9f20-43d3-b8f5-0b198c1dfefc" />


**Question 7**
---
Write a SQL query to identify the top 3 most expensive discounted products. Return product_id, original_price, discount_percentage, and discounted_price.

Sample table: Products

product_id | original_price | discount_percentage

 ------------+----------------+--------------------- 

101 | 50.00 | 0.10 

102 | 150.00 | 0.15 

103 | 200.00 | 0.20 

104 | 300.00 | 0.25
```sql
select product_id, original_price, discount_percentage, original_price - (original_price * discount_percentage) AS discounted_price
from Products
where discount_percentage > 0
order by discounted_price DESC
Limit 3;
```

**Output:**

<img width="1223" height="287" alt="Screenshot 2025-10-15 102726" src="https://github.com/user-attachments/assets/788af506-709c-4239-8234-61b31bc99149" />


**Question 8**
---
Write a SQL query to find employees who were hired after January 1, 2020.

emp table

cid         name        type        
----------  ----------  ---------- 
0           empno       INT         
1           ename       VARCHAR(100)
2           job         VARCHAR(50)
3           mgr         INT        
4           hiredate    DATE        
5           sal         DECIMAL(10,2)  
6           comm        DECIMAL(10,2)  
7           deptno      INT         
```sql
select empno, ename, job,mgr, hiredate, sal, comm, deptno
from emp
where hiredate > '2020-01001';
```

**Output:**

<img width="1225" height="367" alt="Screenshot 2025-10-15 102521" src="https://github.com/user-attachments/assets/a043e11f-a484-49b9-93bc-ef6db56ee914" />


**Question 9**
---
Write a SQL query to Delete a Specific Surgery whose ID is 3

Sample table: Surgeries

attributes: surgery_id, patient_id, surgeon_id, surgery_date
```sql
delete from surgeries
where surgery_id =3;
```

**Output:**

<img width="1210" height="381" alt="Screenshot 2025-10-15 103412" src="https://github.com/user-attachments/assets/d130c438-f74b-40d5-99f3-b936791fd41a" />

**Question 10**
---
Write a SQL statement to Update the product_name to 'Premium Bread' whose product ID is 5 in the products table.

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
update products
set product_name='Premium Bread'
where product_id=5;
```

**Output:**

<img width="1225" height="399" alt="Screenshot 2025-10-15 104742" src="https://github.com/user-attachments/assets/e688b6af-748d-4f68-b12f-5be48d7095f1" />



## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
