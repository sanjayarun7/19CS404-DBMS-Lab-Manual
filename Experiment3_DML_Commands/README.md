<img width="1252" height="388" alt="image" src="https://github.com/user-attachments/assets/2428b912-4bd6-465c-8b39-605f449b1ffd" /># Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
--
Write a SQL statement to Update the product_name to 'Premium Bread' whose product ID is 5 in the products table. Products table

```sql
UPDATE products SET product_name = 'Premium Bread' WHERE product_id = 5;
```

**Output:**
<img width="1453" height="228" alt="image" src="https://github.com/user-attachments/assets/501bd029-fa0d-457e-84a8-442a81ecd9c0" />


**Question 2**
---
Write a SQL statement to Increase the salary by 500 and email as 'updated' for employees with job ID 'SA_REP' and commission percentage greater than 0.15

Employees table

```sql
UPDATE EMPLOYEES SET salary = salary + 500, email = 'updated' WHERE job_id = 'SA_REP' AND commission_pct > 0.15;
```

**Output:**
<img width="1224" height="319" alt="image" src="https://github.com/user-attachments/assets/3bbd66cf-723e-4651-98e9-2b38f798b6d4" />


**Question 3**
---
Update the reorder level to 40 pieces for all products belonging to the 'Grocery' category in the products table.



```sql
UPDATE products SET reorder_lvl = 40 WHERE category = 'Grocery';
```

**Output:**
<img width="1274" height="182" alt="image" src="https://github.com/user-attachments/assets/6aad989c-2b9d-4af0-b1c9-6278b7c42207" />


**Question 4**
---
Write a SQL query to Delete a Specific Surgery whose ID is 3

```sql
DELETE FROM Surgeries WHERE surgery_id = 3;
```

**Output:**



**Question 5**
---
Write a SQL query to Delete customers with 'GRADE' 3 or 'AGENT_CODE' 'A008' whose 'OUTSTANDING_AMT' is less than 5000

```sql
DELETE FROM Customer WHERE (GRADE = 3 OR AGENT_CODE = 'A008') AND OUTSTANDING_AMT < 5000;
```

**Output:**
<img width="1171" height="248" alt="image" src="https://github.com/user-attachments/assets/9a60e64c-ef88-4ff8-bd02-79584ce11e1c" />


**Question 6**
---
Write a SQL statement to Find those salesmen with all information whose name containing the 1st character is 'N' and the 4th character is 'l' and rests may be any character.

```sql
SELECT * FROM salesman WHERE name LIKE 'N__L%';
```

**Output:**
<img width="1249" height="357" alt="image" src="https://github.com/user-attachments/assets/a7953ec6-9480-4d36-854b-18e89878c263" />

**Question 7**
---
Write a SQL query to assess the performance of value2 as 'Poor', 'Average', or 'Excellent' based on whether it is less than 30, between 30 and 70, or greater than 70 in the Calculations table

```sql
SELECT id, value2,
    CASE 
        WHEN value2 < 30 THEN 'Poor'
        WHEN value2 BETWEEN 30 AND 70 THEN 'Average'
        WHEN value2 > 70 THEN 'Excellent'
    END AS performance 
FROM calculations;
```

**Output:**
<img width="949" height="494" alt="image" src="https://github.com/user-attachments/assets/12386031-e596-42f6-b016-90b0c140651c" />


**Question 8**
---
Write a SQL query to find all those customers who does not have any grade. Return customer_id, cust_name, city, grade, salesman_id.

```sql

SELECT customer_id, cust_name, city, grade, salesman_id FROM customer WHERE grade IS NULL;
```

**Output:**
<img width="1252" height="388" alt="image" src="https://github.com/user-attachments/assets/a626cd04-3d60-4007-86b9-63cd539a178a" />


**Question 9**
---
SELECT customer_id, cust_name, city, grade, salesman_id FROM customer WHERE grade IS NULL;

```sql
SELECT customer_id, cust_name, city, grade, salesman_id FROM customer WHERE grade IS NULL;
```

**Output:**
<img width="1252" height="388" alt="image" src="https://github.com/user-attachments/assets/a4b7e239-2ee2-4065-9eaf-63f94d9eadac" />


**Question 10**
---
Find Products with a Discounted Price Greater than a Given Amount:

Write a query to list all products that have a discounted price greater than $100. Return product_id, original_price, discount_percentage, and discounted_price.

Sample table: Products

product_id | original_price | discount_percentage

"101" "50" "0.1"

"102" "150" "0.15"

"103" "200" "0.2"

"104" "300" "0.25"

```sql
SELECT 
    product_id, 
    original_price,
    discount_percentage,
    original_price * (1-discount_percentage) AS discounted_price 
FROM Products
WHERE discounted_price > 100;
```

**Output:**
<img width="1262" height="221" alt="image" src="https://github.com/user-attachments/assets/2f2cb77d-32d4-4499-a4a0-f733e610e633" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
