# SQL-Lab2

# We will use the Employees and Awards table below:

 <img src="Lab2.png" width="500" height="500">

### Q1: Choose all employees who have received an award (Nested Query)?
Query:
```sql
select  * from employee where employee.id in (select awards.employee_id from awards)
```

Output:
 <img src="Q1.png" width="500" height="500">
 

### Q2: Choose all employees who have never received an award (Nested Query)?
Query:
```sql
select  * from employee where
employee.role="Developer" AND employee.salary > (SELECT sum(employee.salary) from employee where employee.role="Manager")
```

Output:
 <img src="Q2.png" width="500" height="500">

 
### Q3: Choose all Developers who make more than all Managers combined (Nested Query)?
Query:
```sql
select  * from employee where
employee.role="Developer" AND employee.salary > (SELECT max(employee.salary) from employee where employee.role="Manager")
```

Output:
 <img src="Q3.png" width="500" height="500">

 
### Q4: Choose all Developers who make more money than any Manager (Nested Query)?
Query:
```sql
select  * from employee where
employee.role="Developer" AND employee.salary > (SELECT employee.salary from employee where employee.role="Manager")
```
Output:

  <img src="Q4.png" width="500" height="500">

### Q5: Choose all employees whose salaries are higher than the average for their position. (Nested Query)?
Query:
```sql
select  * from employee where (
employee.role="Developer" AND employee.salary > (SELECT avg(employee.salary) from employee where employee.role="Developer"))
OR
employee.role="Manager" AND employee.salary > (SELECT avg(employee.salary) from employee where employee.role="Manager")
```

Output:
 <img src="Q5.png" width="500" height="500">
