# SQL Lab – Experiment9

## Aim
To write and execute SQL queries using subqueries and aggregate functions to retrieve employee details such as highest salary, job-wise salary comparison, and department-wise salary analysis.

## Question 1
Display the name of emp name who earns highest salary. 

### Query
```sql
SELECT ENAME FROM EMPLOYEE WHERE SAL = (SELECT MAX(SAL) FROM EMPLOYEE);
```

## Question 2
Display the employee number and name of employee working as clerk and earning highest salary among clerks. 

### Query
```sql
SELECT EMPNO, ENAME FROM EMPLOYEE WHERE JOB = 'CLERK' AND SAL = (SELECT MAX(SAL) FROM EMPLOYEE WHERE JOB = 'CLERK');
```

## Question 3
Display the names of the salesman who earns a salary more than the highest salary of any clerk.

### Query
```sql
SELECT ENAME FROM EMPLOYEE WHERE JOB = 'SALESMAN' AND SAL > (SELECT MAX(SAL) FROM EMPLOYEE WHERE JOB = 'CLERK');
```

## Question 4
Display the names of clerks who earn salary more than that of james of that of sal lesser than that of scott

### Query
```sql
SELECT ENAME FROM EMPLOYEE WHERE JOB = 'CLERK' AND SAL > (SELECT SAL FROM EMPLOYEE WHERE ENAME = 'JAMES') AND SAL < (SELECT SAL FROM EMPLOYEE WHERE ENAME = 'SCOTT');
```

## Question 5
Display the names of employees who earn a sal more than that of james or that of salary greater than that of scott.  

### Query
```sql
SELECT ENAME FROM EMPLOYEE WHERE SAL > (SELECT SAL FROM EMPLOYEE WHERE ENAME = 'JAMES') OR SAL > (SELECT SAL FROM EMPLOYEE WHERE ENAME = 'SCOTT');
```

## Question 6
Display the names of the employees who earn highest salary in their respective departments.

### Query
```sql
SELECT ENAME, DEPTNO, SAL FROM EMPLOYEE E WHERE SAL = (SELECT MAX(SAL) FROM EMPLOYEE WHERE DEPTNO = E.DEPTNO);
```

## Question 7
Display the names of employees who earn highest salaries in their respective job groups.  

### Query
```sql
SELECT ENAME, JOB, SAL FROM EMPLOYEE E WHERE SAL = (SELECT MAX(SAL) FROM EMPLOYEE WHERE JOB = E.JOB);
```

## Question 8
Display the employee names who are working in accounting dept.

### Query
```sql
SELECT ENAME FROM EMPLOYEE WHERE DEPTNO = (SELECT DEPTNO FROM DEPARTMENT WHERE DNAME = 'ACCOUNTING');
```

## Question 9
Display the employee names who are working in chicago.

### Query
```sql
SELECT ENAME FROM EMPLOYEE WHERE DEPTNO = (SELECT DEPTNO FROM DEPARTMENT WHERE LOC = 'CHICAGO');
```

## Question 10
Display the job groups having total salary greater than the maximum salary for managers. 

### Query
```sql
SELECT JOB, SUM(SAL) FROM EMPLOYEE GROUP BY JOB HAVING SUM(SAL) > (SELECT MAX(SAL) FROM EMPLOYEE WHERE JOB = 'MANAGER');
```

   
