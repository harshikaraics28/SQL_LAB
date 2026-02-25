# SQL Lab – Experiment5

## Aim
To study and implement SQL Aggregate Functions and String Functions such as COUNT, SUM, AVG, MIN, MAX, UPPER, LOWER, INITCAP, and LENGTH on the EMPLOYEE table to retrieve summarized and formatted data.

## Question 1
Display the total number of employee working in the company.  

### Query
```sql
SELECT COUNT(*) AS TOTAL_EMPLOYEES FROM EMPLOYEE;
```

## Question 2
Display the total salary being paid to all employees.

### Query
```sql
SELECT SUM(SAL) AS TOTAL_SALARY FROM EMPLOYEE;
```

## Question 3
Display the maximum salary from employee table. 

### Query
```sql
SELECT MAX(SAL) AS MAX_SALARY FROM EMPLOYEE;
```

## Question 4
Display the minimum salary from employee table.

### Query
```sql
SELECT MIN(SAL) AS MIN_SALARY FROM EMPLOYEE;
```

## Question 5
Display the average salary from employee table 

### Query
```sql
SELECT AVG(SAL) AS AVG_SALARY FROM EMPLOYEE;
```

## Question 6
Display the maximum salary being paid to clerk. 

### Query
```sql
SELECT MAX(SAL) AS MAX_SALARY FROM EMPLOYEE WHERE JOB='CLERK';
```

## Question 7
Display the maximum salary being paid in dept no 20. 

### Query
```sql
SELECT MAX(SAL) AS MAX_SALARY FROM EMPLOYEE WHERE DEPTNO=20;
```

## Question 8
Display the minimum salary paid to any salesman. 

### Query
```sql
SELECT MIN(SAL) AS MIN_SALARY FROM EMPLOYEE WHERE JOB='SALESMAN';
```

## Question 9
Display the average salary drawn by managers. 

### Query
```sql
SELECT AVG(SAL) AS AVG_SALARY FROM EMPLOYEE WHERE JOB='MANAGER';
```

## Question 10
Display the total salary drawn by analyst working in dept no 40.

### Query
```sql
SELECT SUM(SAL) FROM EMPLOYEE WHERE JOB = 'ANALYST' AND DEPTNO = 40;
```

## Question 11
Display the names of the employee in Uppercase. 

### Query
```sql
SELECT UPPER(ENAME) FROM EMPLOYEE;
```

## Question 12
Display the names of the employee in Lowercase. 

### Query
```sql
SELECT LOWER(ENAME) FROM EMPLOYEE;
```

## Question 13
Display the names of the employee in Proper case. 

### Query
```sql
SELECT CONCAT(UPPER(LEFT(ENAME,1)),LOWER(SUBSTR(ENAME,2))) FROM EMPLOYEE;
```

## Question 14
Display the length of Your name using appropriate function. 

### Query
```sql
SELECT LENGTH('HARSHIKA') AS NAME_LENGTH;
```

## Question 15
Display the length of all the employee names. 

### Query
```sql
SELECT ENAME, LENGTH(ENAME) AS NAME_LENGTH FROM EMPLOYEE;
```