# Experiment 4: Aggregate Functions, Group By and Having Clause
NAME: SANJAY A
Reg.no: 212224040288
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
How many appointments are scheduled for each doctor?

```sql
SELECT DoctorID, COUNT(*) AS TotalAppointments
FROM Appointments
GROUP BY DoctorID
ORDER BY DoctorID;
```

**Output:**
<img width="715" height="614" alt="image" src="https://github.com/user-attachments/assets/337e015a-778f-48f9-9de9-307c6b5596e7" />


**Question 2**
---
What is the average dosage prescribed for each medication?

```sql
SELECT Medication,AVG(Dosage) AS AvgDosage
FROM Prescriptions
GROUP BY Medication
ORDER BY Medication;
```

**Output:**
<img width="615" height="726" alt="image" src="https://github.com/user-attachments/assets/9de87ace-0957-4f78-8fd5-3d58f8b58817" />


**Question 3**
---
How many patients are there in each city?

```sql
SELECT Address,COUNT(*) AS TotalPatients
FROM Patients
GROUP BY Address
ORDER BY Address;
```

**Output:**
<img width="615" height="391" alt="image" src="https://github.com/user-attachments/assets/d0182b38-1bd6-4da6-b9a9-393e590ef2a8" />


**Question 4**
---
Write a SQL query to return the total number of rows in the 'customer' table where the city is not Noida.

```sql
SELECT COUNT(*) AS COUNT FROM customer
WHERE city!='Noida';
```

**Output:**
<img width="325" height="271" alt="image" src="https://github.com/user-attachments/assets/5342e539-e9f6-47d3-95db-3569bde537a6" />


**Question 5**
---Write a SQL query to calculate the average purchase amount of all orders. Return average purchase amount.

Sample table: orders

ord_no purch_amt ord_date customer_id salesman_id

70001 150.5 2012-10-05 3005 5002

70009 270.65 2012-09-10 3001 5005

70002 65.26 2012-10-05 3002 5001

```sql
SELECT AVG(purch_amt) AS AVERAGE
FROM orders;
```

**Output:**
<img width="343" height="298" alt="image" src="https://github.com/user-attachments/assets/db6120f1-5823-430b-ac2f-e6339d78b8fd" />


**Question 6**
---
Write a SQL query to determine the number of customers who received at least one grade for their activity.

Sample table: customer

customer_id | cust_name | city | grade | salesman_id

```sql
SELECT COUNT(*) AS COUNT FROM customer
WHERE grade IS NOT NULL;
```

**Output:**
<img width="327" height="289" alt="image" src="https://github.com/user-attachments/assets/252435e1-af98-4808-8220-57e3530ee50e" />


**Question 7**
---Write a SQL query to find how many employees have an income greater than 50K?

Table: employee

name type

id INTEGER name TEXT age INTEGER city TEXT income INTEGER

```sql
SELECT COUNT(*) AS employees_count FROM employee
WHERE income>50000;
```

**Output:**
<img width="417" height="299" alt="image" src="https://github.com/user-attachments/assets/064caa57-1648-45ca-9ad4-d9adf8dc8316" />


**Question 8**
---
Write the SQL query that achieves the grouping of data by age intervals using the expression (age/5)5, calculates the total salary sum for each group, and excludes groups where the total salary sum is not greater than 5000.

```sql
SELECT (age/5)*5 AS age_group,SUM(salary)
FROM customer1
GROUP BY age_group
HAVING SUM(salary)>5000;
```

**Output:**
<img width="694" height="412" alt="image" src="https://github.com/user-attachments/assets/5f8c70e2-86a6-40e1-aec4-7bdd6d6bd3b8" />


**Question 9**
---Write the SQL query that achieves the grouping of data by city, calculates the average income for each city, and includes only those cities where the average income is greater than 500,000.

```sql
SELECT city,AVG(income)
FROM employee
GROUP BY city
HAVING AVG(income)>500000;
```

**Output:**
<img width="701" height="499" alt="image" src="https://github.com/user-attachments/assets/f38987a3-f43b-438c-93a7-f813370b6e61" />

**Question 10**
---
Write the SQL query that achieves the grouping of data by occupation, calculates the average work hours for each occupation, and includes only those occupations where the average work hour falls between 10 and 12.

```sql
SELECT occupation,AVG(workhour)
FROM employee1
GROUP BY occupation
HAVING AVG(workhour) BETWEEN 10 AND 12;
```

**Output:**
<img width="763" height="446" alt="image" src="https://github.com/user-attachments/assets/700e9101-e828-401b-94d0-25872dba3cd2" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
