# SQL Lab – Experiment12

## Aim
To write and execute advanced SQL queries involving nested subqueries, relational comparisons, deletion operations, and conditional filtering to analyze employee–manager relationships, department consistency, and salary structures.

## Question 1
Display those employees whose salary is less than his manager but more than salary of any other managers.

### Query
```sql
SELECT E.ENAME, E.SAL FROM EMPLOYEE E WHERE E.SAL < (SELECT M.SAL FROM EMPLOYEE M WHERE M.EMPNO = E.MGR) AND E.SAL > ANY (SELECT SAL FROM EMPLOYEE WHERE JOB = 'MANAGER');
```

## Question 2
Find out the number of employees whose salary is greater than their manager salary? 

### Query
```sql
SELECT COUNT(*) FROM EMPLOYEE E WHERE E.SAL > (SELECT M.SAL FROM EMPLOYEE M WHERE M.EMPNO = E.MGR);
```

## Question 3
Display those managers who are not working under president but they are working under any other manager?

### Query
```sql
SELECT ENAME FROM EMPLOYEE WHERE JOB = 'MANAGER' AND MGR NOT IN (SELECT EMPNO FROM EMPLOYEE WHERE JOB = 'PRESIDENT') AND MGR IS NOT NULL;
```

## Question 4
Delete those department where no employee working?

### Query
```sql
DELETE FROM DEPARTMENT D WHERE NOT EXISTS (SELECT 1 FROM EMPLOYEE E WHERE E.DEPTNO = D.DEPTNO);
```

## Question 5
Delete those records from emp table whose deptno not available in dept table? 

### Query
```sql
DELETE FROM EMPLOYEE WHERE DEPTNO NOT IN (SELECT DEPTNO FROM DEPARTMENT);
```

## Question 6
Display those earners whose salary is out of the grade available in sal grade table?

### Query
```sql
SELECT ENAME, SAL FROM EMPLOYEE E WHERE NOT EXISTS (SELECT 1 FROM SALGRADE S WHERE E.SAL BETWEEN S.LOSAL AND S.HISAL);
```

## Question 7
Display employee name, sal, comm. And whose net pay is greater than any other in the company?

### Query
```sql
SELECT ENAME, SAL, COMM, (SAL + ifnull(COMM,0)) AS NET_PAY FROM EMPLOYEE WHERE (SAL + ifnull(COMM,0)) > ALL (SELECT (SAL + ifnull(COMM,0)) FROM EMPLOYEE);
```

## Question 8
Display those employees who are working in sales or research? 

### Query
```sql
SELECT E.ENAME FROM EMPLOYEE E, DEPARTMENT D WHERE E.DEPTNO = D.DEPTNO AND D.DNAME IN ('SALES', 'RESEARCH');
```

## Question 9
Display the grade of jones?

### Query
```sql
SELECT S.GRADE FROM EMPLOYEE E, SALGRADE S WHERE E.SAL BETWEEN S.LOSAL AND S.HISAL AND E.ENAME = 'JONES';
```

## Question 10
Display the department name the no of characters of which is equal to no of employees in any other department? 

### Query
```sql
SELECT D.DNAME FROM DEPARTMENT D WHERE LENGTH(D.DNAME) IN (SELECT COUNT(*) FROM EMPLOYEE GROUP BY DEPTNO);
```     