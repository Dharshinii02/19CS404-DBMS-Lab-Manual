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
Write a SQL query that retrieves the all the columns from the Table Grades, where the grade is equal to the minimum grade achieved in each subject.

Sample table: GRADES (attributes: student_id, student_name, subject, grade)

```sql

SELECT student_id, student_name, subject, grade
FROM GRADES g1
WHERE grade = (
    SELECT MIN(grade)
    FROM GRADES g2
    WHERE g2.subject = g1.subject
);
```

**Output:**

<img width="1265" height="457" alt="Screenshot 2025-11-10 134647" src="https://github.com/user-attachments/assets/87fae83a-130f-436c-ab99-dfeb084a3b34" />


**Question 2**
---
From the following tables write a SQL query to find the order values greater than the average order value of 10th October 2012. Return ord_no, purch_amt, ord_date, customer_id, salesman_id.

Note: date should be yyyy-mm-dd format


```sql
SELECT *
FROM orders
WHERE purch_amt >
    (SELECT avg(purch_amt)
     FROM orders 
     WHERE ord_date = '2012-10-10');
```

**Output:**

<img width="1269" height="453" alt="Screenshot 2025-11-10 134654" src="https://github.com/user-attachments/assets/91e466c3-e6f7-4487-a98c-a88a417f4081" />



**Question 3**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose Address as Delhi and age below 30

Sample table: CUSTOMERS
```sql
SELECT * FROM CUSTOMERS WHERE ID IN (SELECT ID FROM CUSTOMERS WHERE Address="Delhi" and age <30);
```

**Output:**
<img width="1264" height="360" alt="Screenshot 2025-11-10 134702" src="https://github.com/user-attachments/assets/c799dc0c-f7fd-40bb-9df8-f423f1c179ed" />


**Question 4**
---
From the following tables write a SQL query to count the number of customers with grades above the average in New York City. Return grade and count.

```sql
SELECT grade, COUNT(*)
FROM customer
GROUP BY grade
HAVING grade >
    (SELECT AVG(grade)
     FROM customer
     WHERE city = 'New York');
```

**Output:**
<img width="1260" height="329" alt="Screenshot 2025-11-10 134707" src="https://github.com/user-attachments/assets/7bc7e4de-d758-461c-80e8-56b09777ed1d" />


**Question 5**
---
From the following tables, write a SQL query to find all the orders issued by the salesman 'Paul Adam'. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.
```sql
SELECT *
FROM orders
WHERE salesman_id =
    (SELECT salesman_id 
     FROM salesman 
     WHERE name='Paul Adam');
```

**Output:**

<img width="1273" height="388" alt="Screenshot 2025-11-10 134714" src="https://github.com/user-attachments/assets/a4756f42-7a36-4e15-9071-d91875dbac92" />

**Question 6**
---
Write a query to display all the customers whose ID is the difference between the salesperson ID of Mc Lyon and 2001.

salesman table

name             type
---------------  ---------------
salesman_id      numeric(5)
name                 varchar(30)
city                    varchar(15)
commission       decimal(5,2)
```sql
SELECT *
FROM customer
WHERE customer_id = (
    SELECT salesman_id - 2001
    FROM salesman
    WHERE name = 'Mc Lyon'
);
```

**Output:**
<img width="1260" height="333" alt="Screenshot 2025-11-10 134726" src="https://github.com/user-attachments/assets/3fa7a0ab-d8fa-4ed8-922f-37af17f3e9dc" />



**Question 7**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is LESS than $2500.
```sql
SELECT * FROM CUSTOMERS WHERE ID IN (SELECT ID FROM CUSTOMERS WHERE SALARY < 2500);

```

**Output:**

<img width="1251" height="471" alt="Screenshot 2025-11-10 134757" src="https://github.com/user-attachments/assets/ea18886e-2396-4489-a20f-d480e38b4735" />


**Question 8**
---
From the following tables write a SQL query to find salespeople who had more than one customer. Return salesman_id and name.

```sql
select salesman_id,name from salesman where 
salesman_id in 
(select salesman_id from customer 
GROUP by salesman_id 
HAVING COUNT(customer_id)>1);
```

**Output:**

<img width="902" height="478" alt="Screenshot 2025-11-10 134802" src="https://github.com/user-attachments/assets/4f8467b4-dbbe-4d52-a306-1266bfd4ca2e" />


**Question 9**
---
Write a SQL query to Find employees who have an age less than the average age of employees with incomes over 2.5 Lakh

Employee Table

name             type

------------   ---------------

id                    INTEGER

name              TEXT

age                 INTEGER

city                 TEXT

income           INTEGER

```sql
SELECT *
FROM employee
WHERE age < (SELECT AVG(age) FROM employee WHERE income > 250000);
```

**Output:**

<img width="1266" height="533" alt="Screenshot 2025-11-10 134808" src="https://github.com/user-attachments/assets/162a6359-a730-41d9-9a53-32abb5956c91" />



**Question 10**
---
Write a SQL query that retrieve all the columns from the table "Grades", where the grade is equal to the maximum grade achieved in each subject.

Sample table: GRADES (attributes: student_id, student_name, subject, grade)

```sql
SELECT student_id, student_name, subject, grade
FROM GRADES g1
WHERE grade = (
    SELECT MAX(grade)
    FROM GRADES g2
    WHERE g2.subject = g1.subject
);

```

**Output:**

<img width="1260" height="451" alt="Screenshot 2025-11-10 134814" src="https://github.com/user-attachments/assets/92f2bb3c-e2e3-4a3c-8b11-0797eead8659" />




## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
