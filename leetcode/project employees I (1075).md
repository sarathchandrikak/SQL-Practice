=======================================================
### 1075. Project Employees I (https://leetcode.com/problems/project-employees-i/description)
=======================================================

### Table Schema

#### Table: Project

| Column Name  | Type  |
|-------------|-------|
| project_id  | int   |
| employee_id | int   |

#### Table: Employee

| Column Name      | Type    |
|------------------|---------|
| employee_id      | int     |
| name             | varchar |
| experience_years | int     |


### Question

Write an SQL query that reports the average experience years of all the employees for each project, rounded to 2 digits.

### Solution

```sql
    with cte1 as (
    select p.project_id, e.employee_id,  sum(e.experience_years) as sum_years 
    FROM project p LEFT JOIN employee e on p.employee_id = e.employee_id 
    GROUP BY p.project_id, e.employee_id)

    select project_id, round(avg(sum_years),2) as average_years from cte1 group by project_id
```

### Concepts

The query uses concepts of `CTE` and `JOIN` and to find average experience of years
