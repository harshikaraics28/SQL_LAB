# SQL Lab 

## Aim
To create a database and tables and execute SQL queries using DDL and DML commands.

## Question 1
Creating a database.

### Query
```sql
CREATE DATABASE 2CSE18_32;
```

## Question 2
Selecting required database for further operations.

### Query
```sql
USE 2CSE18_32;
```

## Question 3
Creating table Department.

### Query
```sql
CREATE TABLE department (  deptno INT(2) PRIMARY KEY,  dname VARCHAR(15) NOT NULL);
```

## Question 4
Verifying table structure of Department.

### Query
```sql
DESC department ;
```

## Question 5
Inseting values in Department.

### Query
```sql
INSERT INTO department VALUES (10,'RESEARCH'),(20,'ACCOUNTING'),(30,'SALES'),(40,'OPERATIONS');
```

## Question 6
Verifying inserted data in Department.

### Query
```sql
SELECT * FROM DEPARTMENT;
```

## Question 7
Creating table Employee.

### Query
```sql
CREATE TABLE employee (empno INT(4) PRIMARY KEY, ename VARCHAR(20) NOT NULL, job VARCHAR(20), mgr INT(4), hiredate DATE, sal INT(10), comm INT(7), deptno INT(2),FOREIGN KEY (deptno) REFERENCES department(deptno));
```

## Question 8
Verifying table structure of Employee.

### Query
```sql
DESC EMPLOYEE;
```

## Question 9
Inseting values in Department.

### Query
```sql
INSERT INTO employee (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO) VALUES
(7369, 'SMITH',  'CLERK',     7902, '1980-12-17',  800,  NULL, 20),
(7499, 'ALLEN',  'SALESMAN',  7698, '1981-02-20', 1600,  300,  30),
(7521, 'WARD',   'SALESMAN',  7698, '1981-02-22', 1250,  300,  30),
(7566, 'JONES',  'MANAGER',   7839, '1981-04-02', 2975,  NULL, 20),
(7654, 'MARTIN', 'SALESMAN',  7698, '1981-09-28', 1250, 1400,  30),
(7698, 'BLAKE',  'MANAGER',   7839, '1981-05-01', 2850,  NULL, 30),
(7782, 'CLARK',  'MANAGER',   7839, '1981-06-09', 2450,  NULL, 20),
(7788, 'SCOTT',  'ANALYST',   7566, '1982-12-09', 3000,  NULL, 40),
(7839, 'KING',   'PRESIDENT', NULL, '1981-11-17', 5000,  NULL, 20),
(7844, 'TURNER', 'SALESMAN',  7698, '1981-09-08', 1500,     0, 30),
(7876, 'ADAMS',  'CLERK',     7788, '1983-01-12', 1100,  NULL, 20),
(7900, 'JAMES',  'CLERK',     7698, '1981-12-03',  950,  NULL, 30),
(7902, 'FORD',   'ANALYST',   7566, '1981-12-03', 3000,  NULL, 20),
(7934, 'MILLER', 'CLERK',     7782, '1982-01-23', 1300,  NULL, 10);
```

## Question 10
Verifying the inserted data in employee.

### Query
```sql
SELECT * FROM EMPLOYEE;
```