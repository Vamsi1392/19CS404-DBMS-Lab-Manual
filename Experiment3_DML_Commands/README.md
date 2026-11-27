# Experiment 3: DML Commands

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
Write a SQL statement to Change the supplier name to 'A1 Suppliers' where the supplier ID is 8 in the suppliers table.

Table info

suppliers(supplier_id,supplier_name,contact_person,phone_number,email,address)

For example:

Test	Result
select changes();
changes()
----------
1

```sql
update suppliers
set supplier_name='A1 Suppliers'
where supplier_id like '%8%';
```

**Output:**
<img width="1262" height="182" alt="Screenshot 2026-11-27 210304" src="https://github.com/user-attachments/assets/5f7dc95f-51c5-4ef7-adb5-a3a64667a23d" />


**Question 2**
---
Write a SQL statement to update the product_name as 'Grapefruit' whose product_id is 4 in the products table.

products table

---------------
product_id
product_name
category_id
availability


```sql
UPDATE products
SET product_name = 'Grapefruit'
WHERE product_id = 4
```

**Output:**
<img width="1085" height="216" alt="Screenshot 2026-11-27 210351" src="https://github.com/user-attachments/assets/06957910-0794-4ddd-aa48-b4c9c033ed37" />


**Question 3**
---
Write a SQL statement to Update the product_name to 'Premium Bread' whose product ID is 5 in the products table.

Products table

---------------
product_id
product_name
category
cost_price
sell_price
reorder_lvl
quantity
supplier_id


```sql
UPDATE Products 
set product_name = 'Premium Bread'
where product_id = 5;
```

**Output:**

<img width="1258" height="225" alt="Screenshot 2026-11-27 210455" src="https://github.com/user-attachments/assets/d42aa699-510b-46bf-a75b-ba3054ef9039" />



**Question 4**
---
Write a SQL statement to double the availability of the product with product_id 1.

products table

---------------
product_id
product_name
category_id
availability

```sql
UPDATE products
SET availability = availability * 2
WHERE product_id = 1;
```

**Output:**
<img width="1097" height="212" alt="Screenshot 2026-11-27 210538" src="https://github.com/user-attachments/assets/8c8d3e22-4897-45d2-92e4-c7b85a304116" />


**Question 5**
---
Write a SQL statement to change salary of employee to 8000 whose Employee ID is 105, if the existing salary is less than 5000.

Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id
For example:

Test	Result
SELECT EMPLOYEE_ID, FIRST_NAME, SALARY, PHONE_NUMBER FROM EMPLOYEES WHERE EMPLOYEE_ID=105;
EMPLOYEE_ID  FIRST_NAME  SALARY      PHONE_NUMBER
-----------  ----------  ----------  ------------
105          David       8000        590.423.4569



```sql
UPDATE Employees
SET salary = 8000
WHERE employee_id = 105
  AND salary < 5000;
```

**Output:**
<img width="1332" height="188" alt="Screenshot 2026-11-27 210627" src="https://github.com/user-attachments/assets/220b9a69-b02d-4f19-9ecc-eee71d1972ad" />


**Question 6**
---

Write a SQL query to Delete All Doctors whose ID ranges from 2 to 4.

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization
For example:

Test	Result
SELECT * FROM doctors;
doctor_id   first_name  last_name   specialization
----------  ----------  ----------  --------------
1           John        Smith       Cardiology
2           Emily       Johnson     Orthopedics
3           Michael     Brown       Pediatrics
doctor_id   first_name  last_name   specialization
----------  ----------  ----------  --------------
1           John        Smith       Cardiology


```sql
delete from Doctors
where doctor_id between 2 and 4;
```

**Output:**
<img width="912" height="596" alt="Screenshot 2026-11-27 210715" src="https://github.com/user-attachments/assets/788a80e8-10a8-4b92-b1fc-e940d1784a84" />



**Question 7**
---
Write a SQL query to Delete customers with 'GRADE' 3 or 'AGENT_CODE' 'A008' whose 'OUTSTANDING_AMT' is less than 5000

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |
For example:

Test	Result
select changes();
changes()
----------
1


```sql
DELETE FROM Customer
where( GRADE=3
OR AGENT_CODE='A008')
AND OUTSTANDING_AMT < 5000;

```

**Output:**
<img width="1120" height="150" alt="Screenshot 2026-11-27 210759" src="https://github.com/user-attachments/assets/718bb473-75e2-4ce5-9e05-3bce752c3e27" />



**Question 8**
---

Write a SQL query to Delete All Doctors with a NULL Specialization

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization
For example:

Test	Result
SELECT * FROM doctors;
doctor_id   first_name  last_name   specialization
----------  ----------  ----------  --------------
1           John        Smith       Cardiology
2           Emily       Johnson     Orthopedics
3           Michael     Brown       Pediatrics
4           Febin       Jones
doctor_id   first_name  last_name   specialization
----------  ----------  ----------  --------------
1           John        Smith       Cardiology
2           Emily       Johnson     Orthopedics
3           Michael     Brown       Pediatrics


```sql

DELETE FROM doctors
WHERE specialization IS NULL;
```

**Output:**
<img width="948" height="730" alt="Screenshot 2026-11-27 210855" src="https://github.com/user-attachments/assets/3c0e7e0c-ac39-4cb3-b944-3a6728fb4562" />



**Question 9**
---
Write a SQL query to Delete customers with following conditions

'CUST_COUNTRY' is not in a list of specified countries ('UK', 'USA', 'Canada')
'GRADE' is greater than or equal to 3
Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |
For example:

Test	Result
select changes();
changes()
----------
2



```sql
DELETE FROM Customer
WHERE CUST_COUNTRY NOT IN ('UK', 'USA', 'Canada')
AND GRADE >= 3;
```

**Output:**
<img width="1382" height="197" alt="Screenshot 2026-11-27 210933" src="https://github.com/user-attachments/assets/2ba88926-c46c-444c-bbd6-9d217ecc7fea" />


**Question 10**
---

Write a SQL query to Delete customers from 'customer' table where 'AGENT_CODE' is either 'A003' or 'A008'.

 
Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |
For example:

Test	Result
select distinct(agent_code)from customer;
AGENT_CODE
----------
A003
A008
A011
A006
A005
A010
A002
A004
A009
A007
A012
A001
AGENT_CODE
----------
A011
A006
A005
A010
A002
A004
A009
A007
A012
A001

```sql

DELETE FROM customer
WHERE agent_code IN ('A003', 'A008');
```

**Output:**

<img width="580" height="782" alt="Screenshot 2026-11-27 211013" src="https://github.com/user-attachments/assets/a377848e-489c-43fb-b4fc-0a5a8dc10c18" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
