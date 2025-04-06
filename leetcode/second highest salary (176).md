=======================================================
### 176. Second Highest Salary (https://leetcode.com/problems/second-highest-salary/)
=======================================================

### Table Schema

#### Table: Employee

| Column Name | Type |
|-------------|------|
| id          | int  |
| salary      | int  |

### Question

Write a solution to find the second highest distinct salary from the Employee table. If there is no second highest salary, return NULL

### Solution

```sql
    select COALESCE(max(salary), null) as SecondHighestSalary from Employee where salary < (select max(salary) from employee)
```

### Concepts

The query uses `COALESCE FUNCTION` to fill in NULL Values if there's no second highest salary