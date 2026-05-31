# Experiment 2: DDL Commands
Name: SANJAY A
Reg.no: 212224040288

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
<img width="1205" height="366" alt="image" src="https://github.com/user-attachments/assets/7940d94e-c84a-4e27-bfcd-f62714d4e175" />


**Question 2**
---
```
alter table Companies add column designation varchar(50);
alter table Companies add column net_salary number;
alter table Companies add column dob date;
```



**Output:**
<img width="1185" height="401" alt="image" src="https://github.com/user-attachments/assets/e6f66b4b-c00a-4d08-8f0b-9759bd60b3b7" />

**Question 3**
---
-- Paste Question 3 here

```sql
create table Locations(
LocationID INTEGER,
LocationName TEXT,
Address TEXT
);
```

**Output:**

<img width="1179" height="369" alt="597328837-0b9767ee-8dd2-48bb-917a-2c937a33b045" src="https://github.com/user-attachments/assets/6d1cb550-51b6-4347-aef7-7db60a551f55" />


**Question 4**
---
--Create a table named Orders with the following constraints: OrderID as INTEGER should be the primary key. OrderDate as DATE should be not NULL. CustomerID as INTEGER should be a foreign key referencing Customers(CustomerID).

```sql
create table Orders(
OrderID INTEGER primary key,
OrderDate DATE not null,
CustomerID INTEGER,
foreign key (CustomerID) references Customers(CustomerID)
);
```

**Output:**

<img width="1188" height="272" alt="image" src="https://github.com/user-attachments/assets/8e14d3d8-0008-4560-826b-4401076fd936" />


**Question 5**
---
Create a table named Events with the following columns:

EventID as INTEGER EventName as TEXT EventDate as DATE

```sql
create table Events(
EventID INTEGER,
EventName TEXT,
EventDate DATE
);
```

**Output:**

<img width="1192" height="366" alt="image" src="https://github.com/user-attachments/assets/11a15292-0f77-45fd-89d1-c7ae235aef9b" />


**Question 6**
---
Create a table named Orders with the following columns:
OrderID as INTEGER OrderDate as TEXT CustomerID as INTEGER

```sql
create table Orders(
OrderID INTEGER,
OrderDate TEXT,
CustomerID INTEGER
);
```

**Output:**
<img width="1179" height="363" alt="image" src="https://github.com/user-attachments/assets/e0868442-0d1b-4aff-9ce3-fd779ab8ca39" />


**Question 7**
---
Insert the following products into the Products table:

```sql
insert into Products (Name,Category,Price,Stock)
 values
 ('Smartphone','Electronics',800,150),
 ('Headphones','Accessories',200,300);
```

**Output:**

<img width="1190" height="342" alt="image" src="https://github.com/user-attachments/assets/78c348bd-fb36-4086-9c46-f2aefbdc7a01" />


**Question 8**
---
Insert a student with RollNo 201, Name David Lee, Gender M, Subject Physics, and MARKS 92 into the Student_details table.

```sql
insert into Student_details (RollNo,Name,Gender,Subject,Marks)
values 
(201,'David Lee','M','Physics',92);
```

**Output:**
<img width="1186" height="234" alt="image" src="https://github.com/user-attachments/assets/7cfb4ad5-cb8a-42e8-b90e-9124822e5c6d" />


**Question 9**
---
Write a SQL query to modify the Student_details table by adding a new column Email of type VARCHAR(50) and updating the column MARKS to have a default value of 0.

```sql
ALTER table Student_details add Email varchar(50);
alter table Student_details 
add column MARKS integer default 0;
```

**Output:**
<img width="1180" height="231" alt="image" src="https://github.com/user-attachments/assets/1118c0e7-564d-4822-b712-baa36e290430" />


**Question 10**
Insert all students from Archived_students table into the Student_details table.

```sql
insert into Student_details(RollNo,Name,Gender,Subject,Marks)
select RollNo,Name,Gender,Subject,Marks
from Archived_students;
```

**Output:**
![Uploading image.png…]()

![Output10](output.png)


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
