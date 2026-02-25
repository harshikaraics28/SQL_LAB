# SQL Lab – Experiment3

## Aim
To create the EMPLOYEE and DEPARTMENT tables as per the given constraints and to perform SQL queries using conditions, pattern matching, sorting, arithmetic operations, and logical operators to retrieve required information from the tables.

## Question 1
List all employees and jobs in Department 30 in descending order by salary.  

### Query
```sql
SELECT ENAME, JOB FROM EMPLOYEE WHERE DEPTNO = 30 ORDER BY SAL DESC;
```

## Question 2
List job and Department Number of employees whose name are five letters long begin with “A” and end with “N”.

### Query
```sql
SELECT JOB, DEPTNO FROM EMPLOYEE WHERE ENAME LIKE 'A___N';
```

## Question 3
Display the name of employees whose name start with alphabet S. 

### Query
```sql
SELECT ENAME FROM EMPLOYEE WHERE ENAME LIKE 'S%';
```

## Question 4
Display the names of employees whose name ends with alphabet S. 

### Query
```sql
SELECT ENAME FROM EMPLOYEE WHERE ENAME LIKE '%S';
```

## Question 5
Display the names of employees working in department number 10 or 20 or 40 or employees working as clerks,salesman or analyst.  


### Query
```sql
SELECT ENAME FROM EMPLOYEE WHERE DEPTNO IN (10, 20, 40) OR JOB IN ('CLERK', 'SALESMAN', 'ANALYST');
```

## Question 6
Display employee number and names for employees who earn commission.

### Query
```sql
SELECT EMPNO, ENAME FROM EMPLOYEE WHERE COMM IS NOT NULL;
```

## Question 7
Display employee number and total salary for each employee.

### Query
```sql
SELECT EMPNO, SAL + NVL(COMM, 0) AS TOTAL_SALARY FROM EMPLOYEE;
```

## Question 8
Display employee number and annual salary for each employee.  

### Query
```sql
SELECT EMPNO, SAL * 12 AS ANNUAL_SALARY FROM EMPLOYEE;
```

## Question 9
Display the names of all employees working as clerks and drawing a salary more than 3,000.

### Query
```sql
SELECT ENAME FROM EMPLOYEE WHERE JOB = 'CLERK' AND SAL > 3000;
```

## Question 10
Display the names of employees who are working as clerk,salesman or analyst and drawing a salary more than 3,000. 

### Query
```sql
SELECT ENAME FROM EMPLOYEE WHERE JOB IN ('CLERK', 'SALESMAN', 'ANALYST') AND SAL > 3000;
```