# Experiment 7: PL/SQL – Variables, Control Structures and Loops
# Name: Sanjay a
# reg no:212224040288
## AIM
To write and execute simple PL/SQL programs using variables, loops, and conditional statements.


## THEORY

PL/SQL, which stands for Procedural Language extensions to the Structured Query Language (SQL). It is a combination of SQL along with the procedural features of programming languages.

**Syntax:**
```sql
DECLARE 
   <declarations section> 
BEGIN 
   <executable command(s)>
EXCEPTION 
   <exception handling> 
END;
```

### Basic Components of PL/SQL Block:
- DECLARE: Section to declare variables and constants.
- BEGIN: The execution section that contains PL/SQL statements.
- EXCEPTION: Handles errors or exceptions that occur in the program.
- END: Marks the end of the PL/SQL block.

# PL/SQL Programs – Steps and Expected Output

## 1. Write a PL/SQL program to find the Greatest of Two Numbers

### Steps:
- Declare two numeric variables and initialize them.
- Use an `IF` statement to compare the values.
- Display the greater number using `DBMS_OUTPUT.PUT_LINE`.
  Syntax
  ```
  DECLARE
    num1 NUMBER := 45;   
    num2 NUMBER := 80;   
  BEGIN
    IF num1 > num2 THEN
        DBMS_OUTPUT.PUT_LINE('Greater number is: ' || num1);
    ELSIF num2 > num1 THEN
        DBMS_OUTPUT.PUT_LINE('Greater number is: ' || num2);
    ELSE
        DBMS_OUTPUT.PUT_LINE('Both numbers are equal.');
    END IF;
  END;
  ```


**Expected Output:**  
<img width="291" height="152" alt="image" src="https://github.com/user-attachments/assets/a3f640fc-ccbf-4dc1-8ffa-9cf6aa479108" />


---

## 2. Write a PL/SQL program to Calculate Sum of First N Natural Numbers

### Steps:
- Declare a variable `n` and assign a value (e.g., 10).
- Initialize a `sum` variable to 0.
- Use a `WHILE` loop to iterate from 1 to `n`, adding each number to the sum.
- Display the result using `DBMS_OUTPUT.PUT_LINE`.
# syntax
```
DECLARE
  n   NUMBER := 10;      
  i   NUMBER := 1;
  sum NUMBER := 0;
BEGIN
  WHILE i <= n LOOP
    sum := sum + i;
    i := i + 1;
  END LOOP;

  DBMS_OUTPUT.PUT_LINE('Sum of first ' || n || ' natural numbers is: ' || sum);
END;
/
```

**Expected Output:**  
Sum of first 10 natural numbers is: 55
<img width="403" height="138" alt="image" src="https://github.com/user-attachments/assets/1ac7d510-2130-4fea-9ede-025e9800b356" />

---

## 3. Write a PL/SQL program to generate Fibonacci series

### Steps:
- Declare the variable `n` to indicate how many terms to generate.
- Initialize the first two Fibonacci numbers (0 and 1).
- Use a loop to generate the next terms using the formula `c = a + b`.
- Print each term in the series.

# Syntax
```
DECLARE
    n NUMBER := 7;        -- Number of terms to generate
    a NUMBER := 0;        -- First term
    b NUMBER := 1;        -- Second term
    c NUMBER;             -- Next term
    i NUMBER;             -- Loop counter
BEGIN
    DBMS_OUTPUT.PUT_LINE('n = ' || n);
    DBMS_OUTPUT.PUT('Fibonacci sequence: ');
    
    -- Print first two numbers
    DBMS_OUTPUT.PUT(a || ', ' || b);
    
    -- Loop from 3rd term to nth term
    FOR i IN 3..n LOOP
        c := a + b;
        DBMS_OUTPUT.PUT(', ' || c);
        a := b;
        b := c;
    END LOOP;
    
    DBMS_OUTPUT.NEW_LINE;
END;
/
```

**Expected Output:**  
n = 7  
Fibonacci sequence: 0, 1, 1, 2, 3, 5, 8
<img width="420" height="154" alt="image" src="https://github.com/user-attachments/assets/b0eb3c9a-8672-48b3-83aa-9085ad2dc8f2" />

---

## 4. Write a PL/SQL Program to display the number in Reverse Order

### Steps:
- Declare a variable `n` and assign a value (e.g., 1535).
- Use a loop to extract each digit using modulo and reverse the number.
- Display the reversed number.
Syntax
```
DECLARE
    n NUMBER := 1535;      -- Original number
    rev NUMBER := 0;       -- Variable to store reversed number
    rem NUMBER;            -- To store remainder
    temp NUMBER;           -- Temporary variable
BEGIN
    temp := n;  -- Preserve the original number

    WHILE temp > 0 LOOP
        rem := MOD(temp, 10);               -- Extract last digit
        rev := (rev * 10) + rem;            -- Build reversed number
        temp := FLOOR(temp / 10);           -- Remove last digit
    END LOOP;

    DBMS_OUTPUT.PUT_LINE('n = ' || n);
    DBMS_OUTPUT.PUT_LINE('Reversed number is ' || rev);
END;
/
```
**Expected Output:**  
n = 1535  
Reversed number is 5351
<img width="339" height="165" alt="image" src="https://github.com/user-attachments/assets/9fd5968d-bf32-4f05-a40d-986f40fd3f6b" />

---

## 5. Write a PL/SQL program to find the largest of three numbers

### Steps:
- Declare three numeric variables `a`, `b`, and `c`.
- Use nested `IF-ELSIF-ELSE` conditions to find the largest among the three.
- Display the largest number.

```
DECLARE
  a NUMBER := 10;
  b NUMBER := 9;
  c NUMBER := 15;
  largest NUMBER;
BEGIN
  IF (a > b) AND (a > c) THEN
    largest := a;
  ELSIF (b > a) AND (b > c) THEN
    largest := b;
  ELSE
    largest := c;
  END IF;

  DBMS_OUTPUT.PUT_LINE('a = ' || a || ', b = ' || b || ', c = ' || c);
  DBMS_OUTPUT.PUT_LINE('Largest of three numbers is ' || largest);
END;
/
```

**Expected Output:**  
a = 10, b = 9, c = 15  
Largest of three number is 15
<img width="332" height="144" alt="image" src="https://github.com/user-attachments/assets/a568889f-9bc1-4aab-a871-89f33142c39f" />


## RESULT
Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.
