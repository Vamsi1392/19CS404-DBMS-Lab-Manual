# Experiment 4: Aggregate Functions, Group By and Having Clause

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


<img width="680" height="547" alt="Screenshot 2026-11-27 211450" src="https://github.com/user-attachments/assets/57b798b4-da6b-4c49-a28f-4df320423dac" />


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


<img width="672" height="647" alt="Screenshot 2026-11-27 211540" src="https://github.com/user-attachments/assets/50793b15-4a50-44f1-984f-d0ff0595dd22" />


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


<img width="582" height="357" alt="Screenshot 2026-11-27 211625" src="https://github.com/user-attachments/assets/3be091a3-42b5-4537-a584-583e1cd20559" />


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



<img width="485" height="283" alt="Screenshot 2026-11-27 211711" src="https://github.com/user-attachments/assets/457ec505-3839-4658-8b3d-40789c5fa8a9" />


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



<img width="647" height="285" alt="Screenshot 2026-11-27 211753" src="https://github.com/user-attachments/assets/f5d685e0-53b9-492a-8b85-9018aa57b5b6" />


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

<img width="338" height="303" alt="Screenshot 2026-11-27 211834" src="https://github.com/user-attachments/assets/a667ee0e-bc0e-4305-ba5b-d14ce94620c0" />


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

<img width="367" height="287" alt="Screenshot 2026-11-27 211917" src="https://github.com/user-attachments/assets/37afa8fc-30dc-41a8-bf43-7d2c76bd2257" />


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

<img width="635" height="357" alt="Screenshot 2026-11-27 211959" src="https://github.com/user-attachments/assets/87fa096d-f000-40b9-8f21-b7461e5615f2" />


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

<img width="635" height="357" alt="Screenshot 2026-11-27 211959" src="https://github.com/user-attachments/assets/0fdea394-59fb-4da0-81f3-63ce5c33ae96" />


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


<img width="547" height="393" alt="Screenshot 2026-11-27 212046" src="https://github.com/user-attachments/assets/76c81104-0330-4e24-b9d3-bbdb3bc5b11c" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
