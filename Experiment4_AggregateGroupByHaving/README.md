# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
--
How many prescriptions were written in each frequency category (e.g., once daily, twice daily)?

Sample tablePrescriptions Table



```sql
select Frequency,
COUNT(PrescriptionID) AS
TotalPrescriptions
From Prescriptions
group by Frequency;
```

**Output:**

<img width="1188" height="588" alt="Screenshot 2025-10-29 113616" src="https://github.com/user-attachments/assets/4f70186e-e437-4dc7-9ab6-27334ef7a783" />


**Question 2**
---
What is the most common diagnosis among patients?

```sql
select Diagnosis,COUNT(RecordId) as
DiagnosisCount
from MedicalRecords
group by Diagnosis
order by DiagnosisCount DESC
limit 1;
```

**Output:**

<img width="964" height="353" alt="Screenshot 2025-10-29 113623" src="https://github.com/user-attachments/assets/ba6fe67e-c322-42fa-944b-6cce02c33fd6" />


**Question 3**
---
How many medical records were created in each month?

```sql
select 
     STRFTIME('%Y-%m',Date) as Month,
     COUNT(RecordID) as TotalRecords
from MedicalRecords
Group by Month;
```

**Output:**

<img width="1016" height="491" alt="Screenshot 2025-10-29 113628" src="https://github.com/user-attachments/assets/cad8b814-9a7a-4717-bb7f-61b8c141abe8" />


**Question 4**
---
Write a SQL query to find the youngest employee in the company?

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER
```sql
select name as Employee_Name,age as
Age
from employee
order by age ASC
limit 1;
```

**Output:**

<img width="962" height="379" alt="Screenshot 2025-10-29 113634" src="https://github.com/user-attachments/assets/573f40f7-3f24-4dc3-a5c2-a0358bc5a9c2" />


**Question 5**
---
Write a SQL query to calculate total purchase amount of all orders. Return total purchase amount.

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001

```sql
select SUM(purch_amt) as TOTAL
FROM orders;
```

**Output:**

<img width="1052" height="366" alt="Screenshot 2025-10-29 113638" src="https://github.com/user-attachments/assets/4b83ae1e-f5fc-4bb1-a46e-a2117e75d3b1" />

**Question 6**
---

Write a SQL query to find the number of employees whose age is greater than 32.
 

```sql
select COUNT(id) AS COUNT
FROM employee
where age>32;
```

**Output:**

<img width="948" height="363" alt="Screenshot 2025-10-29 113643" src="https://github.com/user-attachments/assets/9f3b184b-a381-4e06-bc80-496ecd26412a" />

**Question 7**
---
Write a SQL query to find Who has the highest income among employee living in California?

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER

```sql
select name,max(income)
from employee
where city='California'
order by income Desc
limit 1;
```

**Output:**

<img width="921" height="344" alt="Screenshot 2025-10-29 113648" src="https://github.com/user-attachments/assets/0644bc91-8730-4e09-bea3-07d3ba940176" />


**Question 8**
---
Which cities (addresses) in the "customer1" table have an average salary lesser than Rs. 15000
```sql
select address,AVG(salary) as "AVG(salary)"
from customer1
group by address
having AVG(salary)<15000;

```

**Output:**

<img width="1032" height="661" alt="Screenshot 2025-10-29 113659" src="https://github.com/user-attachments/assets/62e989c0-9edf-4d4d-848e-5c4e7541e958" />


**Question 9**
---
Write a SQL query to identify the cities (addresses) where the average salary is greater than Rs. 5000, as per the "customer1" table.

```sql
select address,AVG(salary) as "AVG(salary)"
from customer1
group by address
having AVG(salary)>5000;
```

**Output:**

<img width="997" height="513" alt="Screenshot 2025-10-29 113704" src="https://github.com/user-attachments/assets/5b6d5292-a82a-44ea-abd1-9f902c17cecd" />


**Question 10**
---
Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the average work hours for each date, and excludes dates where the average work hour is not less than 10.

```sql
select jdate,AVG(workhour) as "AVG(workhour)"
from employee1
group by jdate
having AVG(workhour)<10;
```

**Output:**

<img width="809" height="411" alt="Screenshot 2025-10-29 113709" src="https://github.com/user-attachments/assets/36d6cc51-6e23-444c-97af-b822137216fd" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
