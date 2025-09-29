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
Create a new table named item with the following specifications and constraints:
item_id as TEXT and as primary key.
item_desc as TEXT.
rate as INTEGER.
icom_id as TEXT with a length of 4.
icom_id is a foreign key referencing com_id in the company table.
The foreign key should cascade updates and deletes.
item_desc and rate should not accept NULL.
```sql
create table item(
item_id TEXT primary key,
item_desc TEXT not null,
rate INTEGER not null,
icom_id TEXT check (Length(icom_id)=4),
Foreign Key (icom_id) References company(com_id)
on update cascade
on delete cascade
);
```

**Output:**
<img width="1239" height="397" alt="Screenshot 2025-09-29 132609" src="https://github.com/user-attachments/assets/1ec3639f-6c3d-4435-bebe-86dd3c82e87f" />


**Question 2**
---
-Insert all products from Discontinued_products into Products.

Table attributes are ProductID, ProductName, Price, Stock
```sql
insert into Products ('ProductId','ProductName','Price','Stock')
select ProductId,ProductName,Price,Stock from Discontinued_products
```

**Output:**

<img width="1229" height="332" alt="Screenshot 2025-09-29 133024" src="https://github.com/user-attachments/assets/d599df93-c966-49f0-a9cb-5a602b8ccdde" />


**Question 3**
---
Create a table named Products with the following constraints:
ProductID as INTEGER should be the primary key.
ProductName as TEXT should be unique and not NULL.
Price as REAL should be greater than 0.
StockQuantity as INTEGER should be non-negative.

```sql
create table Products(
ProductID integer primary key,
ProductName Text unique not null,
Price Real check(Price>0),
StockQuantity integer check(StockQuantity >=0) );
```

**Output:**

<img width="1231" height="325" alt="Screenshot 2025-09-29 133035" src="https://github.com/user-attachments/assets/a1212aae-7bf2-45f8-84e0-faec2c529b94" />

**Question 4**
---
Write an SQL command can to add a column named email of type TEXT to the customers table

```sql
alter table customers
add column email TEXT;
```

**Output:**

<img width="1234" height="329" alt="Screenshot 2025-09-29 133047" src="https://github.com/user-attachments/assets/748b30d5-36ff-4c82-ab22-d831e4b34104" />

**Question 5**
---
Create a table named Employees with the following constraints:

EmployeeID should be the primary key.
FirstName and LastName should be NOT NULL.
Email should be unique.
Salary should be greater than 0.
DepartmentID should be a foreign key referencing the Departments table.
```sql
create table Employees(
EmployeeID integer primary key,
FirstName varchar(50) not null,
LastName varchar (50) not null,
Email Tect unique,
Salary check (Salary>0),
DepartmentID integer,
foreign key (DepartmentID) references Departments(DepartmentID)
);
```

**Output:**

<img width="1234" height="475" alt="Screenshot 2025-09-29 133055" src="https://github.com/user-attachments/assets/8389963e-6f2e-4db4-89fd-da1dca3517f8" />


**Question 6**
---
Write an SQL query to add a new column salary of type INTEGER to the Employees table, with a CHECK constraint that ensures the value in this column is greater than 0.

```sql
alter table Employees
add column salary INTEGER check (salary>0);
```

**Output:**

<img width="1236" height="337" alt="Screenshot 2025-09-29 133103" src="https://github.com/user-attachments/assets/5f7d492e-58c8-4c87-a33b-c4284f157e09" />



**Question 7**
---
Create a table named Members with the following columns:

MemberID as INTEGER
MemberName as TEXT
JoinDate as DATE

```sql
create table Members (
MemberID INTEGER ,
MemberName TEXT,
JoinDate DATE
);
```

**Output:**

<img width="1233" height="419" alt="Screenshot 2025-09-29 133111" src="https://github.com/user-attachments/assets/ca3abbba-e7c4-4a78-99f5-bbb315e56818" />

**Question 8**
---
Write a SQL Query for inserting the below values in the table Customers

ID               NAME             AGE  ADDRESS     SALARY      
---------------  ---------------  ---  ----------  ----------  
1                Ramesh           32   Ahmedabad   2000
2                Khilan           25   Delhi       1500
3                Kaushik          23   Kota        2000
 
```sql
Insert into Customers (ID, NAME, AGE, ADDRESS, SALARY)
Values (1,'Ramesh', 32, 'Ahmedabad', 2000),
(2,'Khilan', 25, 'Delhi', 1500),
(3,'Kaushik', 23, 'Kota', 2000);
```

**Output:**

<img width="1232" height="329" alt="Screenshot 2025-09-29 133118" src="https://github.com/user-attachments/assets/64fc794c-6476-4381-976a-177e00d10959" />


**Question 9**
---
Create a table named Invoices with the following constraints:

InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
DueDate as DATE should be greater than the InvoiceDate.
Amount as REAL should be greater than 0.
```sql
create table Invoices(
InvoiceID INTEGER primary key,
InvoiceDate DATE,
DueDate DATE check( DueDate > InvoiceDate),
Amount REAL check (Amount>0));
```

**Output:**

<img width="1231" height="327" alt="Screenshot 2025-09-29 133128" src="https://github.com/user-attachments/assets/bd8d150d-1c23-4a75-ab18-5bfc8921e763" />

**Question 10**
---
Insert a new product with ProductID 101, Name Laptop, Category Electronics, Price 1500, and Stock 50 into the Products table.
```sql
insert into Products ('ProductID', 'Name', 'Category', 'Price', 'Stock') values (101, 'Laptop', 'Electronics', 1500, 50);
```

**Output:**

<img width="1252" height="282" alt="Screenshot 2025-09-29 133141" src="https://github.com/user-attachments/assets/64d0d463-cf06-4b27-881c-fb2f102bf8e6" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
