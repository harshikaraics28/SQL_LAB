# SQL Lab – Experiment8

## Aim
To study and implement SQL queries using Aggregate Functions, Group By clause,joins and conditional clauses to retrieve, summarize formatted output generation on the EMPLOYEE table.

## Question 1
Display all employees with their dept name. 

### Query
```sql
SELECT e.ENAME d.DNAME FROM EMPLOYEE e JOIN DEPARTMENT d ON e.DEPTNO = d.DEPTNO;
```

## Question 2
Display those employees whose manager names is jones, and also display their manager name. 

### Query
```sql
SELECT e.ENAME AS EMPLOYEE, m.ENAME AS manager FROM EMPLOYEE e JOIN EMPLOYEE m ON e.MGR = m.EMPNO WHERE m.ENAME = 'JONES';
```

## Question 3
Display employee name, his job, his dept name, his manager name, his grade and make out of an under department wise. 

### Query
```sql
SELECT e.ENAME, e.JOB, d.DNAME, m.ENAME AS manager, s.GRADE FROM EMPLOYEE e JOIN DEPARTMENT d ON e.DEPTNO = d.DEPTNO LEFT JOIN EMPLOYEE m ON e.MGR = m.EMPNO JOIN salgrade s ON e.sal BETWEEN s.losal AND s.hisal;
```

## Question 4
List out all the employees name, job, and salary grade and department name for everyone in the company except ‘clerk’.Sort on salary display he highest salary. 

### Query
```sql
SELECT e.ENAME, e.JOB, s.GRADE, d.DNAME, e.SAL FROM EMPLOYEE e JOIN DEPARTMENT d ON e.DEPTNO = d.DEPTNO JOIN salgrade s ON e.sal BETWEEN s.losal AND s.hisal WHERE e.JOB <> 'CLERK' ORDER BY e.SAL DESC;
```

## Question 5
Display employee name, his job and his manager. Display also employees who are without manager.   

### Query
```sql
SELECT e.ENAME, e.JOB, m.ENAME AS manager FROM EMPLOYEE e LEFT JOIN EMPLOYEE m ON e.MGR = m.EMPNO;
```

## Question 6
List the employee name, job, annual salary, deptno, dept name and grade who earn 36000 a year or who are not clerks.

### Query
```sql
SELECT e.ENAME, e.JOB, e.sal*12 AS annual_salary,e.DEPTNO, d.DNAME, s.GRADE FROM EMPLOYEE e JOIN DEPARTMENT d ON e.DEPNTO = d.DEPTNO JOIN salgrade s ON e.sal BETWEEN s.losal AND s.hisal WHERE e.sal*12 = 36000 OR e.JOB <> 'CLERK';
```

## Question 7
List ename, job, annual sal, deptno, dname and grade who earn 30000 per year and who are not clerks.

### Query
```sql
SELECT e.ENAME, e.JOB, e.sal*12 AS annual_salary,e.DEPTNO, d.DNAME, s.grade FROM EMPLOYEE e JOIN DEPARTMENT d ON e.DEPTNO= d.DEPTNO JOIN salgrade s ON e.sal BETWEEN s.losal AND s.hisal WHERE e.sal*12 = 30000 OR e.JOB <> 'CLERK';
```

## Question 8
List out all employees by name and number along with their manager’s name and number also display ‘no manager’ who has no manager.  

### Query
```sql
SELECT e.EMPNO AS EMPLOYEE_NO, e.ENAME AS EMPLOYEE,m.EMPNO AS MGR_NO, COALESCE(m.ENAME,'NO MANAGER') AS MGR_NAME FROM EMPLOYEE e LEFT JOIN EMPLOYEE m ON e.MGR = m.EMPNO;
```

## Question 9
Select dept name, dept no and sum of sal 

### Query
```sql
SELECT d.DEPTNO, d.DNAME, SUM(e.sal) AS total_salary FROM EMPLOYEE e JOIN DEPARTMENT d ON e.DEPTNO = d.DEPTNO GROUP BY d.DEPTNO, d.DNAME;
```

## Question 10
Display employee number, name and location of the department in which he is working

### Query
```sql
SELECT e.EMPNO, e.ENAME, d.LOC FROM EMPLOYEE e JOIN DEPARTMENT d ON e.DEPTNO = d.DEPTNO;
```

## Question 11
Display employee name and department name for each employee. 

### Query
```sql
SELECT e.ENAME, d.DNAME FROM EMPLOYEE e JOIN DEPARTMENT d ON e.DEPTNO = d.DEPTNO;
```


 