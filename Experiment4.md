# SQL Lab – Experiment4

## Aim
To study and implement advanced SQL queries using conditional operators, date functions, pattern matching, arithmetic expressions, sorting, and update statements on the EMPLOYEE table.

## Question 1
Display the list of employees who have joined the company before 30th June 80 or after 31st Dec 81.

### Query
```sql
SELECT ENAME FROM EMPLOYEE WHERE HIREDATE < '1980-06-30' OR HIREDATE > '1981-12-31';
```

## Question 2
Display the names of employees whose names have second alphabet A in their names. 

### Query
```sql
SELECT ENAME FROM EMPLOYEE WHERE ENAME LIKE '_A%';
```

## Question 3
Display the names of employees whose name is exactly five characters in length 

### Query
```sql
SELECT ENAME FROM EMPLOYEE WHERE LENGTH(ENAME) = 5;
```

## Question 4
Display the names of employees whose names have second alphabet A in their names. 

### Query
```sql
SELECT ENAME FROM EMPLOYEE WHERE SUBSTR(ENAME,2,1) ='A';
```

## Question 5
Display the names of employees who are not working as salesman or clerk or analyst. 

### Query
```sql
SELECT ENAME FROM EMPLOYEE WHERE JOB NOT IN ('SALESMAN','CLERK','ANALYST');
```

## Question 6
Display the name of the employee along with their annual salary (sal*12). The name of the employee earning highest salary should appear first. 

### Query
```sql
SELECT ENAME, SAL*12 AS ANNUAL_SALARY FROM EMPLOYEE ORDER BY ANNUAL_SALARY DESC;
```

## Question 7
Display name, sal, hra, pf, da, totalsal for each employee. The output should be in the order of total sal, hra 15% of sal, da 10% of sal, pf 5% of sal. Total salary will be (sal*hra*da)-pf. 

### Query
```sql
SELECT ENAME,SAL,SAL*0.15 AS HRA,SAL*0.10 AS DA,SAL*0.05 AS PF,(SAL + SAL*0.15 + SAL*0.10 - SAL*0.05) AS TOTAL_SAL FROM EMPLOYEE ORDER BY TOTALSAL;
```

## Question 8
Update the salary of each employee by 10% increment who are not eligible for commission.

### Query
```sql
UPDATE EMPLOYEE SET SAL = SAL + (SAL * 0.10) WHERE COMM IS NULL;
```

## Question 9
Display those employees whose salary is more than 3000 after giving 20% increment. 

### Query
```sql
SELECT ENAME FROM EMPLOYEE WHERE SAL + (SAL * 0.20) > 3000;
```

## Question 10
Display those employees whose salary contains atleast 3 digits.

### Query
```sql
SELECT ENAME FROM EMPLOYEE WHERE LENGTH(SAL) >= 3;
```