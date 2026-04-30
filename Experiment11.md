# SQL Lab – Experiment11

## Aim
To write and execute advanced SQL queries using joins, subqueries, aggregate functions, and conditional clauses to perform operations such as deletion, salary comparison, ranking, and department-wise analysis.

## Question 1
Delete those employees who joined the company before 31 Dec-82 while there dept location is ‘new york’ or ‘chicago’.

### Query
```sql
DELETE FROM EMPLOYEE WHERE HIREDATE < '31-DEC-82' AND DEPTNO IN (SELECT DEPTNO FROM DEPARTMENT WHERE LOCATION IN ('NEW YORK', 'CHICAGO'));
```

## Question 2
Display employee name, job, deptname, location for all who are working as managers.

### Query
```sql
SELECT E.ENAME, E.JOB, D.DNAME, D.LOCATION FROM EMPLOYEE E, DEPARTMENT D WHERE E.DEPTNO = D.DEPTNO AND E.JOB = 'MANAGER';
```

## Question 3
Display name and salary of ford if his sal is equal to high sal of his grade. 

### Query
```sql
SELECT ENAME, SAL FROM EMPLOYEE E, SALGRADE S WHERE E.SAL BETWEEN S.LOSAL AND S.HISAL AND ENAME = 'FORD' AND SAL = (SELECT MAX(SAL) FROM EMPLOYEE E2, SALGRADE S2 WHERE E2.SAL BETWEEN S2.LOSAL AND S2.HISAL AND S.GRADE = S2.GRADE);
```

## Question 4
Find out the top 5 earner of company. 

### Query
```sql
SELECT * FROM (SELECT ENAME, SAL FROM EMPLOYEE ORDER BY SAL DESC) WHERE ROWNUM <= 5;
```

## Question 5
Display the name of those employees who are getting highest salary.

### Query
```sql
SELECT ENAME, SAL FROM EMPLOYEE WHERE SAL = (SELECT MAX(SAL) FROM EMPLOYEE);
```

## Question 6
Display those employees whose salary is equal to average of maximum and minimum. 

### Query
```sql
SELECT ENAME, SAL FROM EMPLOYEE WHERE SAL = (SELECT (MAX(SAL) + MIN(SAL)) / 2 FROM EMPLOYEE);
```

## Question 7
Display dname where at least 3 are working and display only dname 

### Query
```sql
SELECT D.DNAME FROM DEPARTMENT D, EMPLOYEE E WHERE D.DEPTNO = E.DEPTNO GROUP BY D.DNAME HAVING COUNT(E.EMPNO) >= 3;
```

## Question 8
Display name of those managers names whose salary is more than average salary of company. 

### Query
```sql
SELECT ENAME FROM EMPLOYEE WHERE JOB = 'MANAGER' AND SAL > (SELECT AVG(SAL) FROM EMPLOYEE);
```

## Question 9
Display those managers name whose salary is more than an average salary of his employees. 

### Query
```sql
SELECT M.ENAME FROM EMPLOYEE M WHERE M.JOB = 'MANAGER' AND M.SAL > (SELECT AVG(E.SAL) FROM EMPLOYEE E WHERE E.MGR = M.EMPNO);
```

## Question 10
Display employee name, sal, comm and net pay for those employees whose net pay are greater than or equal to any other employee salary of the company? 

### Query
```sql
SELECT ENAME, SAL, COMM, (SAL + IFNULL(COMM,0)) AS NET_PAY FROM EMPLOYEE WHERE (SAL + IFNULL(COMM,0)) >= ANY (SELECT SAL FROM EMPLOYEE);
```  