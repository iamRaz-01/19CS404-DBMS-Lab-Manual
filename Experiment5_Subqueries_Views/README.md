# Experiment 5: Subqueries and Views
### Name : Abdul Rasak N 
### Reg No : 212224240001

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

Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose Address as Delhi and age below 30
```
Sample table: CUSTOMERS

ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------

1          Ramesh       32              Ahmedabad     2000
2          Khilan       25              Delhi       1500
3          Kaushik      23              Kota         2000
4          Chaitali      25             Mumbai       6500
5          Hardik        27              Bhopa        8500
6          Komal         22              Hyderabad    4500
7           Muffy        24              Indore      10000


```
```sql
select * from CUSTOMERS 
where (address='Delhi' and age <30) order by ID asc;
```

**Output:**

![image](https://github.com/user-attachments/assets/a5b1dfa2-9348-4f0c-8ef5-935063378ae2)


**Question 2**
---

From the following tables, write a SQL query to find all the orders issued by the salesman 'Paul Adam'. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.
```
salesman table

name             type
---------------  ---------------
salesman_id      numeric(5)
name             varchar(30)
city             varchar(15)
commission       decimal(5,2)

orders table

name             type
---------------  --------
order_no         int
purch_amt        real
order_date       text
customer_id      int
salesman_id      int
```
```sql
select * from orders 
where salesman_id= (
select salesman_id 
from salesman
where name='Paul Adam'
);
```

**Output:**

![image](https://github.com/user-attachments/assets/2c3c0859-8036-4e62-b025-5fd9e0f1d16a)


**Question 3**
---

Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is LESS than $2500.
```
Sample table: CUSTOMERS

ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------

1          Ramesh     32              Ahmedabad     2000
2          Khilan        25              Delhi      1500
3          Kaushik      23              Kota         2000
4          Chaitali       25             Mumbai      6500
5          Hardik        27              Bhopal      8500
6          Komal         22              Hyderabad   4500
7          Muffy          24              Indore     10000


```
```sql
select * from CUSTOMERS where salary <2500;
```

**Output:**

![image](https://github.com/user-attachments/assets/55cafce6-f184-4329-b0e3-7712eb7367a5)


**Question 4**
---

Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is greater than $1500.
```
Sample table: CUSTOMERS

ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------

1          Ramesh       32              Ahmedabad    2000
2          Khilan       25              Delhi       1500
3          Kaushik      23              Kota         2000
4          Chaitali      25             Mumbai      6500
5          Hardik        27             Bhopal      8500
6          Komal         22             Hyderabad   4500
7          Muffy        24              Indore      10000
```
```sql
select * from CUSTOMERS where salary>1500;
```

**Output:**

![image](https://github.com/user-attachments/assets/3fa4cd13-83f5-487e-9382-4e93465cadd7)


**Question 5**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose AGE is LESS than $30
```
Sample table: CUSTOMERS

ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------

1          Ramesh      32             Ahmedabad     2000
2          Khilan      25             Delhi         1500
3          Kaushik     23             Kota          2000
4          Chaitali    25             Mumbai        6500
5          Hardik      27             Bhopal        8500
6          Komal       22             Hyderabad     4500
7          Muffy       24             Indore        10000
```
```sql
select * from CUSTOMERS where age<30;
```

**Output:**

![image](https://github.com/user-attachments/assets/95bde54c-4969-4843-bbfb-13101baf6d76)

**Question 6**
---

Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is EQUAL TO $1500.
```
Sample table: CUSTOMERS

ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------

1          Ramesh     32              Ahmedabad   2000
2          Khilan     25              Delhi       1500
3          Kaushik    23              Kota        2000
4          Chaitali   25              Mumbai      6500
5          Hardik     27              Bhopal      8500
6          Komal      22              Hyderabad   4500
7          Muffy      24              Indore      10000
```
```sql
select * from CUSTOMERS where salary=1500;
```

**Output:**

![image](https://github.com/user-attachments/assets/9c53abb9-bb4e-40ee-9e4b-3d19db0446fa)


**Question 7**
---

From the following tables, write a SQL query to find all the orders generated in New York city. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.
```
SALESMAN TABLE

name               type
-----------        ----------
salesman_id  numeric(5)
name         varchar(30)
city         varchar(15)
commission   decimal(5,2)

ORDERS TABLE

name            type
----------      ----------
ord_no         int
purch_amt      real
ord_date       text
customer_id    int
salesman_id    int
```
```sql
select * from orders 
where salesman_id in(
select salesman_id 
from salesman 
where city ='New York'
);
```

**Output:**

![image](https://github.com/user-attachments/assets/00334cca-e645-440d-87b4-af72063b61d9)


**Question 8**
---
Write a SQL query to List departments with names longer than the average length

Departments Table (attributes: department_id, department_name)

```sql
select department_id , department_name 
from Departments 
where length(department_name)>(
select avg(length(department_name)) 
from Departments 
);
```

**Output:**

![image](https://github.com/user-attachments/assets/b791a99e-9467-4c3d-a78f-a527629629d1)


**Question 9**
---
From the following tables write a SQL query to find salespeople who had more than one customer. Return salesman_id and name.
```
salesman table

name                 type
---------------   ---------------
salesman_id       numeric(5)
name              varchar(30)
city              varchar(15)
commission        decimal(5,2)

customer table

name              type
-----------       ----------
customer_id   int
cust_name     text
city          text
grade         int
salesman_id   int
```
```sql
select s.salesman_id,s.name
from salesman s
join customer c on s.salesman_id=c.salesman_id
group by s.salesman_id,s.name
having count(c.customer_id)>1;
```

**Output:**

![image](https://github.com/user-attachments/assets/5e05b42d-49da-45c4-b196-d8f7cfed4ede)


**Question 10**
---

Write a SQL query to Retrieve the medications with dosages equal to the lowest dosage

Table Name: Medications (attributes: medication_id, medication_name, dosage)

```sql
select * from Medications where dosage=(select min(dosage) from Medications);
```

**Output:**

![image](https://github.com/user-attachments/assets/31e73b33-bbfa-4c1e-8996-6ddae4cac056)


## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.

![image](https://github.com/user-attachments/assets/00432b40-f03d-434a-8838-ae4fb8085f52)
