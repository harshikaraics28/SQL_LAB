# SQL Lab – Experiment10

## Aim
To perform SQL queries involving multiple conditions, joins, and subqueries to filter employees based on department, manager relationships, salary comparisons, and job roles.

## Question 1
Display the names of employees from department number 10 with salary greater than that of any employee working in other departments. 

### Query
```sql
SELECT ENAME FROM EMPLOYEE WHERE DEPTNO = 10 AND sal > ANY (SELECT sal FROM EMPLOYEE WHERE DEPTNO <> 10);
```

## Question 2
Display the names of employee from department number 10 with salary greater than that of all employee working in other departments. 

### Query
```sql
SELECT ENAME FROM EMPLOYEE WHERE DEPTNO = 10 AND sal > ALL (SELECT sal FROM EMPLOYEE WHERE DEPTNO <> 10);
```

## Question 3
Display the details of employees who are in sales dept and grade is 3.

### Query
```sql
SELECT e.* FROM EMPLOYEE e JOIN DEPARTMENT d ON e.DEPTNO = d.DEPTNO JOIN salgrade s ON e.sal BETWEEN s.losal AND s.hisal WHERE d.DNAME = 'SALES'
AND s.grade = 3;
```

## Question 4
Display those who are not managers and who are managers anyone. 

### Query
```sql
SELECT e.ENAME,
       CASE 
           WHEN e.EMPNO IN (SELECT DISTINCT MGR FROM EMPLOYEE WHERE MGR IS NOT NULL)
           THEN 'MANAGER'
           ELSE 'NOT MANAGER'
       END
FROM EMPLOYEE e;
```

## Question 5
Display those employees whose manager name is jones. 

### Query
```sql
SELECT e.ENAME FROM EMPLOYEE e JOIN EMPLOYEE m ON e.MGR = m.EMPNO WHERE m.ENAME = 'JONES';
```

## Question 6
Display ename who are working in sales dept. 

### Query
```sql
SELECT e.ENAME FROM EMPLOYEE e JOIN DEPARTMENT d ON e.DEPTNO = d.DEPTNO WHERE d.DNAME = 'SALES';
```

## Question 7
Display employee name, deptname, salary and comm. For those sal in between 2000 to 5000 while location is chicago.

### Query
```sql
SELECT e.ENAME, d.DNAME, e.sal, e.COMM FROM EMPLOYEE e JOIN DEPARTMENT d ON e.deptno = d.deptno WHERE e.sal BETWEEN 2000 AND 5000 AND d.LOC = 'CHICAGO';
```

## Question 8
Display those employees whose salary greater than his manager salary.

### Query
```sql
SELECT e.ENAME FROM EMPLOYEE e JOIN EMPLOYEE m ON e.MGR = m.EMPNO WHERE e.sal > m.sal;
```

## Question 9
Display those employees who are working in the same dept where his manager is working.

### Query
```sql
SELECT e.ENAME FROM EMPLOYEE e JOIN EMPLOYEE m ON e.MGR = m.EMPNO WHERE e.deptno = m.deptno;
```

## Question 10
Display grade and employees name for the dept no 10 or 30 but grade is not 4, while joined the company before 31-dec-82.

### Query
```sql
SELECT e.ENAME, s.grade FROM EMPLOYEE e JOIN salgrade s ON e.sal BETWEEN s.losal AND s.hisal WHERE e.DEPTNO IN (10, 30) AND s.grade <> 4 AND e.hiredate < '31-DEC-82';
```



