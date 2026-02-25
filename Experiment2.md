# SQL Lab – Experiment2

## Aim
To retrieve data from the Employee table using SQL SELECT queries with conditions, operators, and filtering clauses.

## Question 1
List all distinct jobs in Employee.

### Query
```sql
SELECT DISTINCT Job FROM Employee;
```

## Question 2
List all information about employee in Department Number 30. 

### Query
```sql
SELECT * FROM Employee WHERE DeptNo = 30;
```

## Question 3
Find all department number with department names greater than 20. 

### Query
```sql
SELECT DeptNo FROM Department WHERE DeptNo > 20;
```

## Question 4
Find all information about all the managers as well as the clerks in department 30. 

### Query
```sql
SELECT * FROM Employee WHERE DeptNo = 30 AND (Job = 'MANAGER' OR Job = 'CLERK');
```

## Question 5
List the Employee name, Employee numbers and department of all clerks. 

### Query
```sql
SELECT EmpNo, EName, DeptNo FROM Employee WHERE Job = 'CLERK';
```

## Question 6
Find all managers not in department 30.

### Query
```sql
SELECT * FROM Employee WHERE Job = 'MANAGER' AND DeptNo <> 30;
```

## Question 7
List information about all Employees in department 10 who  are not manager or clerks. 

### Query
```sql
SELECT * FROM Employee WHERE DeptNo = 10 AND Job NOT IN ('MANAGER','CLERK');
```

## Question 8
Find Employees and jobs earning between 1200 and 1400. 

### Query
```sql
SELECT EName, Job, Sal FROM Employee WHERE Sal BETWEEN 1200 AND 1400;
```

## Question 9
List Name and Department Number of employee who are clerks, analyst or salesman. 

### Query
```sql
SELECT EName, DeptNo FROM Employee WHERE Job IN ('CLERK','ANALYST','SALESMAN');
```

## Question 10
List Name and Department Number of employee whose names began with M. 

### Query
```sql
SELECT EName, DeptNo FROM Employee WHERE EName LIKE 'M%';
```