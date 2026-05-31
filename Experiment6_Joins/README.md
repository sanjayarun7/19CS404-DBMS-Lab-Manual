# Experiment 6: Joins
# Name: Sanjay A
# reg.no: 212224040288

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
<img width="1268" height="735" alt="image" src="https://github.com/user-attachments/assets/4bc33709-f1ef-416a-9794-0ca5744aea1f" />


```sql
SELECT patients.first_name, surgeries.*
FROM patients
INNER JOIN surgeries
ON patients.patient_id = surgeries.patient_id
WHERE patients.date_of_birth > '1990-01-01';
```

**Output:**
<img width="1295" height="289" alt="image" src="https://github.com/user-attachments/assets/81aeec49-e293-4c25-9f50-3b4349163bf6" />


**Question 2**
---
<img width="1294" height="778" alt="image" src="https://github.com/user-attachments/assets/4b9195c6-5b36-4dd3-9204-d1385d213c84" />

```sql
SELECT orders.ord_no, 
       orders.purch_amt, 
       orders.ord_date, 
       customer.cust_name, 
       customer.city AS customer_city, 
       customer.grade, 
       salesman.name AS salesman_name, 
       salesman.city AS salesman_city, 
       salesman.commission
FROM orders
INNER JOIN customer ON orders.customer_id = customer.customer_id
INNER JOIN salesman ON orders.salesman_id = salesman.salesman_id;
```

**Output:**
<img width="1361" height="613" alt="image" src="https://github.com/user-attachments/assets/fd7f72d9-670f-4b61-acf8-b94d30e9b855" />

**Question 3**
---
<img width="1310" height="633" alt="image" src="https://github.com/user-attachments/assets/49b63155-d5ea-4179-9e41-554a7d8d6f5c" />


```sql
SELECT customer.cust_name, 
       customer.city AS city, 
       customer.grade, 
       salesman.name AS Salesman, 
       salesman.city AS city
FROM customer
INNER JOIN salesman ON customer.salesman_id = salesman.salesman_id
WHERE customer.grade < 300
ORDER BY customer.customer_id ASC;
```

**Output:**
<img width="1301" height="509" alt="image" src="https://github.com/user-attachments/assets/01350a30-31b6-499a-8a5b-2919ab627774" />


**Question 4**
---
<img width="1299" height="576" alt="image" src="https://github.com/user-attachments/assets/41126b44-19e8-4e28-8a8c-cb4fb6c545b4" />


```sql
SELECT n.nurse_id, d.department_name
FROM nurses n
INNER JOIN departments d ON n.department_id = d.department_id
WHERE n.first_name = 'David' AND n.last_name = 'Moore';
```

**Output:**
<img width="1097" height="309" alt="image" src="https://github.com/user-attachments/assets/526ddcba-3738-47b0-9dbf-76c11a5b5674" />


**Question 5**
---
<img width="1259" height="813" alt="image" src="https://github.com/user-attachments/assets/aeb8dbc2-fc67-42d6-9d2d-4f7a926296aa" />


```sql
SELECT o.ord_no, o.ord_date, o.purch_amt, c.cust_name AS "Customer Name", c.grade, s.name AS Salesman, s.commission
FROM orders o
INNER JOIN customer c ON o.customer_id = c.customer_id
INNER JOIN salesman s ON o.salesman_id = s.salesman_id;
```

**Output:**
<img width="1326" height="609" alt="image" src="https://github.com/user-attachments/assets/57f4c7c4-f0a1-42a3-aee0-200d590f59a2" />


**Question 6**
---
<img width="1321" height="584" alt="image" src="https://github.com/user-attachments/assets/8431057f-c412-4047-a54e-95b4daa5c721" />


```sql
SELECT c.*
FROM customer c
LEFT JOIN orders o ON c.customer_id = o.customer_id
WHERE o.ord_date > '2012-08-17';
```

**Output:**

<img width="1279" height="629" alt="image" src="https://github.com/user-attachments/assets/5caa7cd0-cab0-48a3-b08d-bd91ea8fdc9d" />


**Question 7**
---
<img width="1307" height="579" alt="image" src="https://github.com/user-attachments/assets/fb4aebfb-7353-4ee1-ae31-d917db26e281" />


```sql
SELECT c.cust_name, s.name
FROM customer c
LEFT JOIN salesman s ON c.salesman_id = s.salesman_id
WHERE c.city = s.city;
```

**Output:**
<img width="1166" height="481" alt="image" src="https://github.com/user-attachments/assets/72ed9f2e-7331-4607-87f9-2632fd9fad15" />


**Question 8**
---
<img width="1222" height="782" alt="image" src="https://github.com/user-attachments/assets/fdff728e-6c5b-4df8-a434-408f1bf9c0a9" />


```sql
SELECT c.cust_name AS "Customer Name", 
       c.city AS "city", 
       s.name AS "Salesman", 
       s.commission AS "commission"
FROM customer c
JOIN salesman s ON c.salesman_id = s.salesman_id;
```

**Output:**
<img width="1211" height="730" alt="image" src="https://github.com/user-attachments/assets/335735a7-8c85-4cf8-95e8-fe006131d51e" />


**Question 9**
---
<img width="1283" height="640" alt="image" src="https://github.com/user-attachments/assets/0f20fd7d-93f8-41c3-8e98-9a491de431ad" />


```sql
SELECT n.*
FROM nurses n
INNER JOIN departments d ON n.department_id = d.department_id
WHERE d.department_name = 'Pediatrics';
```

**Output:**
<img width="1234" height="308" alt="image" src="https://github.com/user-attachments/assets/356f0c17-307a-4fe8-9553-e6b68af3e04d" />


**Question 10**
---
<img width="1321" height="727" alt="image" src="https://github.com/user-attachments/assets/598716c5-bae3-4226-99a3-2259a4eb5517" />


```
SELECT c.cust_name as "Customer Name", c.city AS city, s.name AS Salesman, s.city AS city, s.commission
FROM customer c
INNER JOIN salesman s ON c.salesman_id = s.salesman_id
WHERE c.city != s.city
AND s.commission > 0.12;
```

**Output:**
<img width="1263" height="463" alt="image" src="https://github.com/user-attachments/assets/dd46d251-6c24-45d1-a65b-e8e1f0968da0" />



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
