# SQL Lab – Experiment6

## Aim
To study and implement SQL Date Functions, Conversion Functions, DECODE function, formatting functions, and string/date manipulation queries on the EMPLOYEE table.


## Question 1
Display empno, ename, deptno from employee table. Instead of display department numbers display the related department name (Use decode function). 

### Query
```sql
SELECT EMPNO, ENAME,DECODE(DEPTNO,
              10, 'RESEARCH',
              20, 'ACCOUNTING',
              30, 'SALES',
              40, 'OPERATIONS') AS DNAME FROM EMPLOYEE;
```

## Question 2
Display your age in days.

### Query
```sql
SELECT DATEDIFF('2026-02-17','2007-01-22') AS AGE_IN_DAYS;
```

## Question 3
Display your age in months. 

### Query
```sql
SELECT TIMESTAMPDIFF(MONTH,'2007-01-22',CURDATE()) AS MONTHS;
```

## Question 4
Display the current date as 15th August Friday Nineteen Ninety-Seven. 

### Query
```sql
SELECT DATE_FORMAT('1997-08-15','%D%M%W%Y') AS FORMATTED_DATE;
```

## Question 7
Find the date for nearest Saturday after current date.

### Query
```sql
SELECT DATE_ADD('2026-02-25',INTERVAL (7-DAYOFWEEK('2026-02-25'))DAY) AS NEXT_SATURDAY;
```

## Question 8
Display current time. 

### Query
```sql
SELECT CURTIME();
```

## Question 9
Display the date three months Before the current date 

### Query
```sql
SELECT DATE_SUB(CURDATE(),INTERVAL 3 MONTH);
```

## Question 10
Display those employees who joined in the company in the month of Dec. 

### Query
```sql
SELECT ENAME FROM EMPLOYEE WHERE MONTH(HIREDATE)=12;
```

## Question 13
Display those employees who joined the company before 15 of the months.

### Query
```sql
SELECT ENAME FROM EMPLOYEE WHERE DAY(HIREDATE)<15;
```

## Question 14
Display those employees who has joined before 15th of the month 

### Query
```sql
SELECT ENAME FROM EMPLOYEE WHERE DAY(HIREDATE)<15;
```

## Question 15
Display those employees whose joining DATE is available in deptno 

### Query
```sql
SELECT ENAME FROM EMPLOYEE WHERE DEPTNO LIKE CONCAT('%',DAY(HIREDATE),'%');
```