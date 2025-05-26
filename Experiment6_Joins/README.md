# Experiment 6: Joins

### Name : Abdul Rasak N 
### Reg No : 212224240001

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
Write the SQL query that achieves the selection of all columns from the "patients" table and the specialization from the "doctors" table (aliased as "doctor_specialization"), with an inner join on the "doctor_id" column.
```
PATIENTS TABLE:
name             type
---------------  ---------------
patient_id       INT
first_name       VARCHAR(50)
last_name        VARCHAR(50)
date_of_birth    DATE
admission_date   DATE
discharge_date   DATE
doctor_id        INT

DOCTORS TABLE:

name             type
---------------  ---------------
doctor_id        INT
first_name       VARCHAR(50)
last_name        VARCHAR(50)
specialization   VARCHAR(100)
```
```sql
select p.patient_id,p.first_name,p.last_name,
p.date_of_birth,p.admission_date,p.discharge_date,
p.doctor_id,d.specialization as doctor_specialization
from patients p inner join doctors d 
on p.doctor_id = d.doctor_id;
```

**Output:**

![image](https://github.com/user-attachments/assets/73160b16-89ce-4fb0-b509-b80cd3267de3)


**Question 2**
---
Write the SQL query that achieves the selection of all columns from the "customer" table (aliased as "c"), with a left join on the "customer_id" column and a condition filtering for orders with an order date between '2012-08-01' and '2012-08-30'.

CUSTOMER TABLE:
![unnamed](https://github.com/user-attachments/assets/bc3721c2-5e11-430a-87cf-d46a9ca31d5a)

ORDERS TABLE:
![unnamed](https://github.com/user-attachments/assets/39b8c6f0-56c7-472a-88f0-4fee27a053a9)


```sql
select c.* from customer c
left join orders o
on c.customer_id = o.customer_id
where o.ord_date BETWEEN '2012-08-01' AND '2012-08-30';
```

**Output:**

![image](https://github.com/user-attachments/assets/6bc0cbb1-8633-4151-9508-b56340273cbe)


**Question 3**
---
From the following tables write a SQL query to locate those salespeople who do not live in the same city where their customers live and have received a commission of more than 12% from the company. Return Customer Name, customer city, Salesman, salesman city, commission.  
```
Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
        3008 | Julian Green   | London     |   300 |        5002
        3004 | Fabian Johnson | Paris      |   300 |        5006
        3009 | Geoff Cameron  | Berlin     |   100 |        5003
        3003 | Jozy Altidor   | Moscow     |   200 |        5007
        3001 | Brad Guzan     | London     |       |        5005
Sample table: salesman

 salesman_id |    name    |   city   | commission 
-------------+------------+----------+------------
        5001 | James Hoog | New York |       0.15
        5002 | Nail Knite | Paris    |       0.13
        5005 | Pit Alex   | London   |       0.11
        5006 | Mc Lyon    | Paris    |       0.14
        5007 | Paul Adam  | Rome     |       0.13
        5003 | Lauson Hen | San Jose |       0.12
```
```sql
SELECT 
    c.cust_name AS 'Customer Name',
    c.city AS city,
    s.name AS Salesman,
    s.city AS city,
    s.commission
FROM 
    customer c
JOIN 
    salesman s ON c.salesman_id = s.salesman_id
WHERE 
    c.city <> s.city
    AND s.commission > 0.12;

```

**Output:**

![image](https://github.com/user-attachments/assets/d79b977e-a5db-4f6a-bcd2-655f95c4d35b)

**Question 4**
---
 From the following tables write a SQL query to find the salesperson(s) and the customer(s) he represents. Return Customer Name, city, Salesman, commission.
```
Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
        3008 | Julian Green   | London     |   300 |        5002
        3004 | Fabian Johnson | Paris      |   300 |        5006
        3009 | Geoff Cameron  | Berlin     |   100 |        5003
        3003 | Jozy Altidor   | Moscow     |   200 |        5007
        3001 | Brad Guzan     | London     |       |        5005
Sample table: salesman

 salesman_id |    name    |   city   | commission 
-------------+------------+----------+------------
        5001 | James Hoog | New York |       0.15
        5002 | Nail Knite | Paris    |       0.13
        5005 | Pit Alex   | London   |       0.11
        5006 | Mc Lyon    | Paris    |       0.14
        5007 | Paul Adam  | Rome     |       0.13
        5003 | Lauson Hen | San Jose |       0.12
```
```sql
select 
c.cust_name as 'Customer Name',
c.city ,
s.name as Salesman,
s.commission
from customer c 
join salesman s
on c.salesman_id = s.salesman_id;
```

**Output:**

![image](https://github.com/user-attachments/assets/f693d893-0bea-47e5-9875-3f0fd3132666)


**Question 5**
---
 From the following tables write a SQL query to find salespeople who received commissions of more than 12 percent from the company. Return Customer Name, customer city, Salesman, commission.  
```
Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
        3008 | Julian Green   | London     |   300 |        5002
        3004 | Fabian Johnson | Paris      |   300 |        5006
        3009 | Geoff Cameron  | Berlin     |   100 |        5003
        3003 | Jozy Altidor   | Moscow     |   200 |        5007
        3001 | Brad Guzan     | London     |       |        5005
Sample table: salesman

 salesman_id |    name    |   city   | commission 
-------------+------------+----------+------------
        5001 | James Hoog | New York |       0.15
        5002 | Nail Knite | Paris    |       0.13
        5005 | Pit Alex   | London   |       0.11
        5006 | Mc Lyon    | Paris    |       0.14
        5007 | Paul Adam  | Rome     |       0.13
        5003 | Lauson Hen | San Jose |       0.12
```
```sql
select 
c.cust_name as 'Customer Name',
c.city ,
s.name as Salesman,
s.commission
from customer c 
join salesman s
on c.salesman_id = s.salesman_id
where commission > 0.12;
```

**Output:**

![image](https://github.com/user-attachments/assets/1ce8a0d6-b080-4937-9267-d26eae44fc2b)


**Question 6**
---
From the following tables write a SQL query to find those orders where the order amount exists between 500 and 2000. Return ord_no, purch_amt, cust_name, city.
```
Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
        3008 | Julian Green   | London     |   300 |        5002
        3004 | Fabian Johnson | Paris      |   300 |        5006
        3009 | Geoff Cameron  | Berlin     |   100 |        5003
        3003 | Jozy Altidor   | Moscow     |   200 |        5007
        3001 | Brad Guzan     | London     |       |        5005
Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id
----------  ----------  ----------  -----------  -----------
70001       150.5       2012-10-05  3005         5002
70009       270.65      2012-09-10  3001         5005
70002       65.26       2012-10-05  3002         5001
70004       110.5       2012-08-17  3009         5003
70007       948.5       2012-09-10  3005         5002
70005       2400.6      2012-07-27  3007         5001
70008       5760        2012-09-10  3002         5001
70010       1983.43     2012-10-10  3004         5006
70003       2480.4      2012-10-10  3009         5003
70012       250.45      2012-06-27  3008         5002
70011       75.29       2012-08-17  3003         5007
70013       3045.6      2012-04-25  3002         5001
```
```sql
select o.ord_no,
o.purch_amt,
c.cust_name,
c.city 
from orders o
join customer c 
on c.customer_id=o.customer_id
where o.purch_amt between 500 and 2000;
```

**Output:**

![image](https://github.com/user-attachments/assets/9cfe17cf-8006-4179-b940-c23a37d8a36b)


**Question 7**
---
Write the SQL query that achieves the selection of all columns from the "patients" table, with an inner join on the "doctor_id" column, and includes a condition filtering for patients whose doctors have the first name 'John' and last name 'Smith'.
```
PATIENTS TABLE:
name             type
---------------  ---------------
patient_id       INT
first_name       VARCHAR(50)
last_name        VARCHAR(50)
date_of_birth    DATE
admission_date   DATE
discharge_date   DATE
doctor_id        INT

DOCTORS TABLE:

name             type
---------------  ---------------
doctor_id        INT
first_name       VARCHAR(50)
last_name        VARCHAR(50)
specialization   VARCHAR(100)
```
```sql
select p.*
from patients p
inner join doctors d
on p.doctor_id=d.doctor_id
where d.first_name='John' and d.last_name='Smith';
```

**Output:**

![image](https://github.com/user-attachments/assets/1e03c53a-76f4-41b8-be0c-1879a728a0df)


**Question 8**
---
Write the SQL query that achieves the selection of all columns from the "nurses" table (aliased as "n") and the "department_name" column from the "departments" table, with an inner join on the "department_id" column.

NURSES TABLE:

ATTRIBUTES - nurse_id, first_name, last_name, department_id
![unnamed](https://github.com/user-attachments/assets/09c6046b-4853-447a-85ef-1681e77b25e2)

DEPARTMENTS TABLE:

ATTRIBUTES - department_id, department_name
![unnamed](https://github.com/user-attachments/assets/c1f89a65-8fc6-4a3b-86dd-d9e84dbddbe3)



```sql
select n.*, d.department_name
from nurses n inner join departments d
on n.department_id=d.department_id;
```

**Output:**

![image](https://github.com/user-attachments/assets/c83608ee-f339-4ab6-bacb-c3c5978b6edc)


**Question 9**
---
From the following tables write a SQL query to display the customer name, customer city, grade, salesman, salesman city. The results should be sorted by ascending customer_id.  
```
Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
        3008 | Julian Green   | London     |   300 |        5002
        3004 | Fabian Johnson | Paris      |   300 |        5006
        3009 | Geoff Cameron  | Berlin     |   100 |        5003
        3003 | Jozy Altidor   | Moscow     |   200 |        5007
        3001 | Brad Guzan     | London     |       |        5005
Sample table: salesman

 salesman_id |    name    |   city   | commission 
-------------+------------+----------+------------
        5001 | James Hoog | New York |       0.15
        5002 | Nail Knite | Paris    |       0.13
        5005 | Pit Alex   | London   |       0.11
        5006 | Mc Lyon    | Paris    |       0.14
        5007 | Paul Adam  | Rome     |       0.13
        5003 | Lauson Hen | San Jose |       0.12
```
```sql
select c.cust_name, c.city,c.grade,s.name as 'Salesman', s.city
from customer c join salesman s
on c.salesman_id = s.salesman_id
order by c.customer_id;
```

**Output:**

![image](https://github.com/user-attachments/assets/9bee88c0-8cbf-428f-b93a-ca623af901da)

**Question 10**
---
Write the SQL query that achieves the selection of the "cust_name" and "city" columns from the "customer" table (aliased as "c"), and the "ord_no," "ord_date," and "purch_amt" columns from the "orders" table (aliased as "o"), with a left join on the "customer_id" column and a condition filtering for customers in the city 'London'.

CUSTOMER TABLE:
![unnamed](https://github.com/user-attachments/assets/72d0c223-8824-4bde-8ec3-9a526011b15c)

ORDERS TABLE:
![unnamed](https://github.com/user-attachments/assets/a8bce826-9e41-4735-b152-733fd6f12be4)


```sql
select c.cust_name, c.city ,o.ord_no,o.ord_date,o.purch_amt
from customer c left join orders o
on c.customer_id=o.customer_id
where c.city='London';
```

**Output:**

![image](https://github.com/user-attachments/assets/18369021-c0e3-45b2-a60b-11cf5a8a0987)


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.

![image](https://github.com/user-attachments/assets/a8089300-a37e-424f-bd2a-95578e4f5182)
