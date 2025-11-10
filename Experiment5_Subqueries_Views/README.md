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
From the following tables write a SQL query to find those customers with a grade less than 300. Return cust_name, customer city, grade, Salesman, salesmancity. The result should be ordered by ascending customer_id. 

Sample table: customer

```sql
SELECT
    c.cust_name,
    c.city AS "city",
    c.grade,
    s.name AS "Salesman",
    s.city AS "city"
FROM
    customer c

JOIN
    salesman s ON c.salesman_id = s.salesman_id

WHERE
    c.grade < 300

ORDER BY
    c.customer_id ASC;
```

**Output:**

<img width="1287" height="790" alt="Screenshot 2025-11-10 131823" src="https://github.com/user-attachments/assets/55151797-fd73-4ca8-aaea-3c1a0c7cc379" />


**Question 2**
---
Write the SQL query that accomplishes the selection of the first name and last name from the "patients" table, with an inner join on the "patient_id" column and a condition filtering for surgeries with a surgery date between '2024-01-01' and '2024-01-31'.

PATIENTS TABLE:

```sql
SELECT
    p.first_name,
    p.last_name
FROM
    patients p
INNER JOIN
    surgeries s ON p.patient_id = s.patient_id
WHERE
    s.surgery_date BETWEEN '2024-01-01' AND '2024-01-31';
```

**Output:**

<img width="949" height="401" alt="Screenshot 2025-11-10 131834" src="https://github.com/user-attachments/assets/3b4210ea-ea63-42a5-9fe8-45f10cd32535" />


**Question 3**
---
From the following tables write a SQL query to locate those salespeople who do not live in the same city where their customers live and have received a commission of more than 12% from the company. Return Customer Name, customer city, Salesman, salesman city, commission.  

Sample table: customer

```sql

SELECT
    c.cust_name AS "Customer Name",
    c.city AS "city",
    s.name AS "Salesman",
    s.city AS "city",
    s.commission
FROM
    customer c

JOIN
    salesman s ON c.salesman_id = s.salesman_id

WHERE

    s.commission > 0.12
AND
   c.city <> s.city;
```

**Output:**

<img width="1155" height="630" alt="Screenshot 2025-11-10 131842" src="https://github.com/user-attachments/assets/d1266bbf-c8cb-446a-b58e-f9d8dcca8c8f" />


**Question 4**
---
Write the SQL query that achieves the selection of the "cust_name" column from the "customer" table (aliased as "c"), and the "ord_no," "ord_date," and "purch_amt" columns from the "orders" table (aliased as "o"), with a left join on the "customer_id" column and a condition filtering for orders with a purchase amount greater than 1000.

'customer' Table: (customer_id, cust_name, city, grade, salesman_id)

'orders' Table: (ord_no, purch_amt, ord_date, customer_id, salesman_id)

```sql
SELECT
    c.cust_name,
    o.ord_no,
    o.ord_date,
    o.purch_amt
FROM
    customer c
LEFT JOIN
    orders o ON c.customer_id = o.customer_id
WHERE
    
    o.purch_amt > 1000;
```

**Output:**

<img width="1169" height="708" alt="Screenshot 2025-11-10 131856" src="https://github.com/user-attachments/assets/f6c685ee-36b9-4937-b322-c5d26c26a7b5" />


**Question 5**
---
From the following tables write a SQL query to display the customer name, customer city, grade, salesman, salesman city. The results should be sorted by ascending customer_id.  

Sample table: customer

```sql
SELECT
    c.cust_name,
    c.city AS "city",
    c.grade,
    s.name AS "Salesman",
    s.city AS "city"
FROM
    customer c

JOIN
    salesman s ON c.salesman_id = s.salesman_id

ORDER BY
    c.customer_id ASC;
```

**Output:**

<img width="1299" height="939" alt="Screenshot 2025-11-10 131910" src="https://github.com/user-attachments/assets/d2282cae-fea8-41df-a035-65dbaba103d8" />

**Question 6**
---
Write the SQL query that achieves the selection of the "cust_name" and "city" columns from the "customer" table (aliased as "c"), and the "ord_no," "ord_date," and "purch_amt" columns from the "orders" table (aliased as "o"), with a left join on the "customer_id" column and a condition filtering for customers in the city 'London'.

'customer' Table: (customer_id, cust_name, city, grade, salesman_id)

'orders' Table: (ord_no, purch_amt, ord_date, customer_id, salesman_id)
```sql

SELECT 
    c.cust_name,
    c.city,
    o.ord_no,
    o.ord_date,
    o.purch_amt
FROM customer AS c
LEFT JOIN orders AS o
       ON c.customer_id = o.customer_id
WHERE c.city = 'London';
```

**Output:**
<img width="1286" height="520" alt="Screenshot 2025-11-10 131918" src="https://github.com/user-attachments/assets/771717e5-6d6f-415f-8911-ee0ec078d947" />



**Question 7**
---
Write the SQL query that accomplishes the selection of the first name from the "patients" table and all columns from the "surgeries" table, with an inner join on the "patient_id" column and a condition filtering for patients with the first name 'Alice'.
```sql
SELECT 
    p.first_name,
    s.*
FROM patients AS p
INNER JOIN surgeries AS s
        ON p.patient_id = s.patient_id
WHERE p.first_name = 'Alice';

```

**Output:**

<img width="1299" height="408" alt="Screenshot 2025-11-10 131927" src="https://github.com/user-attachments/assets/1b619ca6-042d-4c42-897d-86e0b6c049d7" />


**Question 8**
---
Write a SQL statement to join the tables salesman, customer and orders so that the same column of each table appears once and only the relational rows are returned. 

```sql
SELECT
    o.ord_no,
    o.purch_amt,
    o.ord_date,
    c.cust_name,
    c.city AS customer_city,
    c.grade,
    s.name AS salesman_name,    
    s.city AS salesman_city,   
    s.commission                
FROM orders o
JOIN customer c
    ON o.customer_id = c.customer_id 
JOIN salesman s
    ON o.salesman_id = s.salesman_id; 
```

**Output:**

<img width="1256" height="906" alt="Screenshot 2025-11-10 131942" src="https://github.com/user-attachments/assets/4b2490ed-c5e1-45bf-afc7-b7dffd80e8bd" />


**Question 9**
---
From the following tables write a SQL query to find the details of an order. Return ord_no, ord_date, purch_amt, Customer Name, grade, Salesman, commission. 



```sql
SELECT
    o.ord_no,
    o.ord_date,
    o.purch_amt,
    c.cust_name AS "Customer Name", -- Retrieves the customer name
    c.grade,
    s.name AS Salesman,             -- Retrieves the salesman's name
    s.commission
FROM orders o
JOIN customer c ON o.customer_id = c.customer_id
JOIN salesman s ON o.salesman_id = s.salesman_id;
```

**Output:**

<img width="1268" height="895" alt="Screenshot 2025-11-10 131956" src="https://github.com/user-attachments/assets/1963965c-6b7f-4e9a-aa0e-f518f3fd2728" />


**Question 10**
---
Write the SQL query that achieves the selection of all columns from the "patients" table (aliased as "p"), with an inner join on the "patient_id" column and a condition filtering for appointments with an appointment date between '2024-01-01' and '2024-01-31'.

PATIENTS TABLE:

ATTRIBUTES - patient_id, first_name, last_name, date_of_birth, admission_date, discharge_date, doctor_id

```sql
SELECT 
    p.*
FROM patients AS p
INNER JOIN appointments AS a
        ON p.patient_id = a.patient_id
WHERE a.appointment_date BETWEEN '2024-01-01' AND '2024-01-31';

```

**Output:**

<img width="1266" height="417" alt="Screenshot 2025-11-10 132007" src="https://github.com/user-attachments/assets/d976f05c-41af-4b2c-9e00-5e8368188854" />



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
