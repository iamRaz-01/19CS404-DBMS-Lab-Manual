# Experiment 2: DDL Commands
### Name :  Abdul Rasak N 
### Reg No : 212224240001

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
--
 Create a table named Invoices with the following constraints:

InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
DueDate as DATE should be greater than the InvoiceDate.
Amount as REAL should be greater than 0.

```sql
create table Invoices (
InvoiceID integer primary key,
InvoiceDate date,
DueDate date check( DueDate> InvoiceDate),
Amount REAL check(Amount>0)
);
```

**Output:**

![image](https://github.com/user-attachments/assets/fd47060c-d10d-4ea6-a8a5-b1f9207c94cc)


**Question 2**
---
Create a table named Attendance with the following constraints:
AttendanceID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
AttendanceDate as DATE.
Status as TEXT should be one of 'Present', 'Absent', 'Leave'.

```sql
create table Attendance(
AttendanceID integer primary key,
EmployeeID integer ,
AttendanceDate date,
Status text check (Status in ('Present','Absent','Leave')),
foreign key (EmployeeID) references Employees(EmployeeID)
)
```

**Output:**

![image](https://github.com/user-attachments/assets/532be113-a80e-45b1-9fe8-b84747722016)


**Question 3**
---
Insert a product with ProductID 104, Name Tablet, and Category Electronics into the Products table, where Price and Stock should use default values.

```sql
insert into Products ('ProductId','Name','Category') values (104,'Tablet','Electronics');
```

**Output:**

![image](https://github.com/user-attachments/assets/f21eac70-99ba-48f6-bcd7-b45a19191c75)


**Question 4**
---
In the Employee table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.
```
EmployeeID  Name          Position    Department  Salary
----------  ------------  ----------  ----------  ----------
5           George Clark  Consultant
7           Noah Davis    Manager     HR          60000
8           Ava Miller    Consultant  IT
```
```sql
insert into Employee ('EmployeeID','Name','Position','Department','Salary') values
(5,'George Clark','Consultant',null,null),
(7,'Noah Davis','Manager','HR',60000),
(8,'Ava Miller','Consultant','IT',null)
```

**Output:**

![image](https://github.com/user-attachments/assets/4c55bd4f-3e29-4fc4-97d0-03e080c1c1af)


**Question 5**
---
Write an SQL query to add two new columns, designation and net_salary, to the table Companies. The designation column should have a data type of varchar(50), and the net_salary column should have a data type of number.

```sql
alter table Companies add column designation varchar(50);
alter table Companies add column net_salary number;
```

**Output:**

![image](https://github.com/user-attachments/assets/282d48b2-a26a-4854-8eac-fcc2ee71dda8)


**Question 6**
---
Create a table named Invoices with the following constraints:
InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
Amount as REAL should be greater than 0.
DueDate as DATE should be greater than the InvoiceDate.
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).

```sql
create table Invoices(
InvoiceID integer primary key,
InvoiceDate date,
Amount real check( Amount>0),
DueDate date check(DueDate > InvoiceDate),
OrderID integer,
foreign key (OrderId) references Orders(OrderId)
)
```

**Output:**

![image](https://github.com/user-attachments/assets/51afbd43-a61b-4cec-927e-8f24f1f7c1b6)


**Question 7**
---
Create a table named Locations with the following columns:

LocationID as INTEGER
LocationName as TEXT
Address as TEXT

```sql
create table Locations(
LocationID INTEGER,
LocationName TEXT,
Address TEXT
)
```

**Output:**

![image](https://github.com/user-attachments/assets/bb0318ec-2dcc-43de-bcf4-d5092c57841f)


**Question 8**
---
Write an SQL Query to add the attributes designation, net_salary, and dob to the Companies table with the following data types:
designation as VARCHAR(50)
net_salary as NUMBER
dob as DATE

```sql
alter table Companies add column designation varchar(50);
alter table Companies add column net_salary number;
alter table Companies add column dob date;
```

**Output:**

![image](https://github.com/user-attachments/assets/523a75bb-84ee-474a-9554-af33830cc376)


**Question 9**
---
Insert all products from Discontinued_products into Products.

Table attributes are ProductID, ProductName, Price, Stock

```sql
insert into Products ('productID','ProductName','Price','Stock') 
select productID, ProductName, Price, Stock from Discontinued_products;
```

**Output:**

![image](https://github.com/user-attachments/assets/446b5c3a-36fe-46cb-9594-9078ace77a49)


**Question 10**
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
LastName varchar(50) not null,
Email text UNIQUE,
Salary check (Salary>0),
DepartmentID integer,
foreign key (DepartmentID) references Departments(DepartmentID)
);
```

**Output:**

![image](https://github.com/user-attachments/assets/dcf40a59-b440-49c8-b3fc-af4de501437d)


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.

![image](https://github.com/user-attachments/assets/941c9436-584f-46ad-8680-9265033aefa3)
