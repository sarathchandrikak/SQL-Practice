=======================================================
### 1789. Primary Department for Each Employee (https://leetcode.com/problems/primary-department-for-each-employee/description)
=======================================================

### Table Schema

#### Table: Employee

| Column Name   |  Type   |
|---------------|---------|
| employee_id   | int     |
| department_id | int     |
| primary_flag  | varchar |


### Question

Write a solution to report all the employees with their primary department. For employees who belong to one department, report their only department.

### Solution

```sql
    select employee_id, department_id 
        from Employee where primary_flag = 'Y'
    UNION 
    select 
        employee_id, department_id 
        from Employee group by employee_id having count(employee_id) = 1
```

### Concepts

The query uses concepts of `UNION, COUNT`, and `FILTER` to find employees who belong to only one environment