# Experiment 4: Aggregate Functions, Group By and Having Clause

### Name : Abdul Rasak N 
### Reg No : 212224240001

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
What is the most common diagnosis among patients?

Sample table:MedicalRecords Table

```sql
select Diagnosis ,count(*) as DiagnosisCount from MedicalRecords 
group by Diagnosis order by DiagnosisCount desc limit 1;
```

**Output:**


![image](https://github.com/user-attachments/assets/16fe4d3c-ebf7-4fc3-a9d1-7bbddfc51ed4)


**Question 2**
---
How many prescriptions were written by each doctor?

Sample tablePrescriptions Table

```sql
select DoctorID , count(*) as TotalPrescriptions from Prescriptions group by DoctorID;
```

**Output:**


![image](https://github.com/user-attachments/assets/92f3916d-3e47-42d2-97da-5fa3cc5fa4f4)


**Question 3**
---
How many medical records are there for each patient?

Sample table:MedicalRecords Table

```sql
select PatientID , count(*) as TotalRecords from MedicalRecords group by PatientID;
```

**Output:**


![image](https://github.com/user-attachments/assets/eed92081-9000-4574-8b6b-ae1629d241a9)


**Question 4**
---
Write a SQL query to find the total number of unique cities in the customer table?
```
Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT
city        TEXT
email       TEXT
phone       INTEGER
```
```sql
select count(*) as unique_cities from customer ;
```

**Output:**


![image](https://github.com/user-attachments/assets/c844439d-93b2-403f-a6e3-8c7c73c1b306)


**Question 5**
---
Write a SQL query to find the youngest employee in the company?
```
Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER
```
```sql
select name as Employee_Name, min(age) as Age from employee;
```

**Output:**


![image](https://github.com/user-attachments/assets/437c2858-8e4e-4dc9-be64-114430770819)


**Question 6**
---
Write a SQL query to find how many employees have an income greater than 50K?
```
Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER
```
```sql
select count(*) as employees_count from employee where income>50000;
```

**Output:**


![image](https://github.com/user-attachments/assets/80b9a83d-1fd8-49b3-8d04-b0cf83a3e337)


**Question 7**
---
Write a SQL query to calculate the average purchase amount of all orders. Return average purchase amount.
```
Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001
```
```sql
select avg(purch_amt) as AVERAGE from orders;
```

**Output:**

![image](https://github.com/user-attachments/assets/95596239-ec51-4c6c-88b6-2852484bf11a)


**Question 8**
---
Write the SQL query that accomplishes the grouping of data by addresses, calculates the sum of salaries for each address, and excludes addresses where the total salary sum is not greater than 2000.

Sample table: customer1

```sql
select address, SUM(salary) 
from customer1 
group by address
having sum(salary)>2000;
```

**Output:**


![image](https://github.com/user-attachments/assets/945fe34e-b490-4686-a62f-feafba8127cf)


**Question 9**
---
Write the SQL query that achieves the selection of product names and the maximum price for each category from the "products" table, and includes only those products where the maximum price is greater than 15.

Sample table: products

```sql
select category_id,product_name,  max(Price) as Price from products group by category_id having price>15; 
```

**Output:**


![image](https://github.com/user-attachments/assets/c1853a4f-b565-4e06-860d-b312346339ef)


**Question 10**
---
Write the SQL query that accomplishes the grouping of data by age intervals using the expression (age/5)5, calculates the minimum age for each group, and excludes groups where the minimum age is not less than 25.

Sample table: customer1

```sql

select (age/5)*5 as age_group,MIN(age) from customer1 group by age_group having min(age)<25;

```

**Output:**

![image](https://github.com/user-attachments/assets/8d294a67-2104-4e0a-9da4-91aab8879e33)


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.

![image](https://github.com/user-attachments/assets/e03675b1-d30d-4726-89bb-38791bb48bdd)
