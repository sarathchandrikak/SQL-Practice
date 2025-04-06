=======================================================
### 185. Department Top Three Salaries (https://leetcode.com/problems/department-top-3-salaries/description)
=======================================================

### Table Schema

#### Table: Employee

| Column Name  | Type    |
|--------------|---------|
| id           | int     |
| name         | varchar |
| salary       | int     |
| departmentId | int     |
 

#### Table: Department

| Column Name | Type    |
|-------------|---------|
| id          | int     |
| name        | varchar |


### Question

Write a solution to find the employees who are high earners in each of the departments.

### Solution

```sql
    SELECT d.name AS Department, e.name AS Employee, e.salary AS Salary
        FROM Employee e
        JOIN Department d ON e.departmentId = d.id
        WHERE e.salary IN (
            SELECT DISTINCT salary 
            FROM Employee e2 
            WHERE e2.departmentId = e.departmentId 
            ORDER BY e2.salary DESC 
            LIMIT 3
        )
```

### Concepts

The query uses concepts of `SUBQUERIES` and `DISTINCT` function to get top 3 salaries from each department