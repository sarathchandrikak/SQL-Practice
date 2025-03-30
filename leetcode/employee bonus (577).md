=======================================================
### 577. Employee Bonus (https://leetcode.com/problems/employee-bonus/description/)
=======================================================


### Table Schema

#### Table: Employee  

| Column Name | Type    |  
|------------|---------|  
| empId      | int     |  
| name       | varchar |  
| supervisor | int     |  
| salary     | int     |  

#### Table: Bonus  

| Column Name | Type |  
|------------|------|  
| empId      | int  |  
| bonus      | int  |  


### Question

Write a solution to report the name and bonus amount of each employee with a bonus less than 1000.

### Solution

```sql
    select e.name, b.bonus from employee e left join bonus b on e.empId = b.empId
    where b.bonus < 1000 or b.bonus is NULL
```

### Concepts

The query uses a `LEFT JOIN` operation and `FILTER` based on given condition
