# SQL Lab – Experiment7

## Aim
To study and implement SQL Aggregate Functions, Group By clause, reporting queries, date calculations, matrix queries, and formatted output generation on the EMPLOYEE table.

## Question 1
Compute the no. of days remaining in this year. 

### Query
```sql
SELECT DATEDIFF('2026-12-31',CURDATE());
```

## Question 2
Find the highest and lowest salaries and the difference between of them. 

### Query
```sql
SELECT MAX(SAL) AS HIGHEST_SAL,MIN(SAL) AS LOWEST_SAL,(MAX(SAL)-MIN(SAL))AS DIFFERENCE FROM EMPLOYEE;
```

## Question 3
List employee whose commission is greater than 25 % of their salaries.  

### Query
```sql
SELECT * FROM EMPLOYEE WHERE COMM > (SAL*0.25);
```

## Question 4
Make a query that displays salary in dollar format. 

### Query
```sql
SELECT ENAME,CONCAT('$',FORMAT(SAL,2)) AS DOLLARS FROM EMPLOYEE;
```

## Question 5
Create a matrix query to display the job, the salary for that job based on department number, and the total salary for that job for all departments, giving each column an appropriate heading. 

### Query
```sql
SELECT JOB,SUM(CASE WHEN DEPTNO=10 THEN SAL ELSE 0 END) AS DEPT10,
        SUM(CASE WHEN DEPTNO=20 THEN SAL ELSE 0 END) AS DEPT20,
        SUM(CASE WHEN DEPTNO=30 THEN SAL ELSE 0 END) AS DEPT30,
        SUM(CASE WHEN DEPTNO=40 THEN SAL ELSE 0 END) AS DEPT40,SUM(SAL) AS TOTAL_SAL FROM  EMPLOYEE GROUP BY JOB;
```

## Question 6
Query that will display the total no of employees, and of that total the number who were hired in 1980,1981,1982 and 1983.Give appropriate column heading. 

### Query
```sql
SELECT COUNT(*),SUM(CASE WHEN YEAR(HIREDATE)=1980 THEN HIREDATE ELSE 0 END) AS EMPLOYEE_1980,
                SUM(CASE WHEN YEAR(HIREDATE)=1981 THEN HIREDATE ELSE 0 END) AS EMPLOYEE_1981,
                SUM(CASE WHEN YEAR(HIREDATE)=1982 THEN HIREDATE ELSE 0 END) AS EMPLOYEE_1982,
                SUM(CASE WHEN YEAR(HIREDATE)=1983 THEN HIREDATE ELSE 0 END) AS EMPLOYEE_1983 FROM EMPLOYEE;
```

## Question 7
Query to get the last Sunday of Any Month. 

### Query
```sql
SELECT LAST_DAY(SYSDATE) - TO_CHAR(LAST_DAY(SYSDATE),'D') + 1 AS LAST_SUNDAY FROM EMPLOYEE;
```

## Question 8
Display department numbers and total number of employees working in each department. 

### Query
```sql
SELECT DEPTNO,COUNT(*) AS TOTAL_EMPLOYEE FROM EMPLOYEE GROUP BY DEPTNO;
```

## Question 9
Display the various jobs and total number of employees within each job group. 

### Query
```sql
SELECT JOB,COUNT(*) AS TOTAL_EMPLOYEE FROM EMPLOYEE GROUP BY JOB;
```

## Question 10
Display the depart numbers and total salary for each department.

### Query
```sql
SELECT DEPTNO,SUM(SAL) AS TOTAL_SAL FROM EMPLOYEE GROUP BY DEPTNO;
```