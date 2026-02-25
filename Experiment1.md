# SQL Lab – Experiment1

## Aim
To perform DDL and DML operations such as creating, deleting, updating, altering, and dropping tables using SQL commands.

## Question 1
Create Employee_master table with data using Employee table.

### Query
```sql
CREATE TABLE Employee_master AS SELECT * FROM Employee;
```

## Question 2
Delete all record into Employee_master whose DeptNo is 10

### Query
```sql
DELETE FROM Employee_master WHERE DeptNo = 10;
```

## Question 3
Update 10% increase in salary of employees whose DeptNo is 20.

### Query
```sql
UPDATE Employee_master SET Sal = Sal + (Sal * 0.10) WHERE DeptNo = 20;
```

## Question 4
Alter SAL column size to 10,2 in Employee_master.

### Query
```sql
ALTER TABLE Employee_master MODIFY Sal DECIMAL(10,2);
```

## Question 5
Drop Employee_master table.

### Query
```sql
DROP TABLE Employee_master;
```


