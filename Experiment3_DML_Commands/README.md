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
How many appointments are scheduled for each doctor?

Sample table:Appointments Table



For example:

Result
DoctorID    TotalAppointments
----------  -----------------
3           3
4           2
6           1
7           3
10          1


```sql
SELECT DoctorID, COUNT(*) AS TotalAppointments
FROM Appointments
GROUP BY DoctorID
ORDER BY DoctorID;
```

**Output:**
<img width="755" height="547" alt="Screenshot 2026-11-27 204542" src="https://github.com/user-attachments/assets/da864a57-1810-408b-bb17-e48275d34aef" />


**Question 2**
---
What is the total number of medications prescribed for each patient?

Sample tablePrescriptions Table



For example:

Result
PatientID   TotalMedications
----------  ----------------
1           1
2           1
3           1
4           1
5           1
6           1
7           1
8           1
9           1
10          1


```sql
select PatientID, COUNT(Medication) as TotalMedications
from Prescriptions
group by PatientID;
```

**Output:**

<img width="757" height="648" alt="Screenshot 2026-11-27 204629" src="https://github.com/user-attachments/assets/3d7147d0-d052-4de6-a23f-76a182ce3d88" />

**Question 3**
---
How many patients are there in each city?

Sample table: Patients Table



For example:

Result
Address     TotalPatients
----------  -------------
Berlin      3
Chicago     4
Mexico      3


```sql
select Address , count(*) as TotalPatients
from Patients
group by Address;
```

**Output:**

<img width="697" height="376" alt="Screenshot 2026-11-27 204717" src="https://github.com/user-attachments/assets/da69cda4-190c-4277-b624-388ac2f1d7d8" />


**Question 4**
---
Write a SQL query to find how many employees have an income greater than 50K?

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER
For example:

Result
employees_count
---------------
8


```sql
SELECT COUNT(*) AS employees_count
FROM employee
WHERE income>50000;
```

**Output:**
<img width="656" height="298" alt="Screenshot 2026-11-27 204800" src="https://github.com/user-attachments/assets/bf9220a6-a6e4-43b1-8f99-9d0b5856045d" />


**Question 5**
---
Write a SQL query to find the customer with longest name?

Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT
city        TEXT
email       TEXT
phone       INTEGER
For example:

Result
name          length
------------  ----------
Preeti Patel  12


```sql
SELECT name, LENGTH(name) AS length
FROM customer
ORDER BY length DESC
LIMIT 1;
```

**Output:**

<img width="682" height="290" alt="Screenshot 2026-11-27 204846" src="https://github.com/user-attachments/assets/66bdfd62-713d-4e02-86fd-49dea7b2bc3c" />


**Question 6**
---
Write a SQL query to calculate the average purchase amount of all orders. Return average purchase amount.

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001

 

For example:

Result
AVERAGE
----------
1461.765


```sql
select avg(purch_amt) as AVERAGE from orders
```

**Output:**

<img width="456" height="288" alt="Screenshot 2026-11-27 204934" src="https://github.com/user-attachments/assets/93432cd4-741d-4ebd-83fb-89449eea1820" />


**Question 7**
---
Write a SQL query to find the maximum purchase amount.

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001

 

For example:

Result
MAXIMUM
----------
5760.0


```sql
SELECT MAX(purch_amt) as MAXIMUM
FROM orders;

```

**Output:**
<img width="457" height="292" alt="Screenshot 2026-11-27 205016" src="https://github.com/user-attachments/assets/c7196cf9-3ddc-41c2-b976-3b89a0369aeb" />


**Question 8**
---
Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the total work hours for each date, and excludes dates where the total work hour sum is not greater than 40.

Sample table: employee1



For example:

Result
jdate       SUM(workhour)
----------  -------------
2004.0      46
2006.0      46


```sql
SELECT jdate, SUM(workhour)
FROM employee1
GROUP BY jdate
HAVING SUM(workhour) > 40;
```

**Output:**

<img width="986" height="351" alt="Screenshot 2026-11-27 205104" src="https://github.com/user-attachments/assets/288a66b2-b5ca-4c18-baa3-4a69dadde571" />


**Question 9**
---
Write the SQL query that achieves the grouping of data by age, calculates the minimum income for each age group, and includes only those age groups where the minimum income is less than 1,000,000.

Sample table: employee



For example:

Result
age         Income
----------  ----------
32          200000
40          350000
45          450000


```sql
SELECT 
    age,
    MIN(Income) AS Income
FROM 
    employee
GROUP BY 
    age
HAVING 
    MIN(Income) < 1000000;
```

**Output:**
<img width="606" height="386" alt="Screenshot 2026-11-27 205145" src="https://github.com/user-attachments/assets/533561b9-1c4b-40fc-9f25-fb8b33ebe64e" />


**Question 10**
---
Write the SQL query that achieves the grouping of data by occupation, calculates the average work hours for each occupation, and includes only those occupations where the average work hour falls between 10 and 12.

Sample table: employee1



For example:

Result
occupation  AVG(workhour)
----------  -------------
Business    10.0
Engineer    12.0


```sql
SELECT 
    occupation,
    AVG(workhour) AS `AVG(workhour)`
FROM 
    employee1
GROUP BY 
    occupation
HAVING 
    AVG(workhour) BETWEEN 10 AND 12;
```

**Output:**
<img width="1292" height="340" alt="Screenshot 2026-11-27 205235" src="https://github.com/user-attachments/assets/3040ec8d-0f99-4701-a4ab-702f0d7c5df4" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
