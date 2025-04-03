=======================================================
### 1731. The Number of Employees Which Report to Each Employee (https://leetcode.com/problems/the-number-of-employees-which-report-to-each-employee/description)
=======================================================

### Table Schema

#### Table: Employees

| Column Name | Type     |
|-------------|----------|
| employee_id | int      |
| name        | varchar  |
| reports_to  | int      |
| age         | int      |

### Question

Write a solution to report the ids and the names of all managers, the number of employees who report directly to them, and the average age of the reports rounded to the nearest integer.

### Solution

```sql
    with cte1 as (
        select 
                reports_to, 
                count(reports_to) as reports_count, 
                ROUND(avg(age)) as average_age
            from Employees group by reports_to)
        select 
                e.employee_id, e.name, ct.reports_count, 
                ct.average_age from Employees e left join cte1 ct on e.employee_id = ct.reports_to 
                where reports_count >= 1 
                order by e.employee_id
```

### Concepts

The query uses concepts of `CTE, COUNT, AVG` and `JOIN` to find number of employees who directly report to manager