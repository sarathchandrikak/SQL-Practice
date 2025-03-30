=======================================================
### 1280. Managers with at least 5 Direct Reports (https://leetcode.com/problems/managers-with-at-least-5-direct-reports)
=======================================================

### Table Schema

#### Table: Employee

| Column Name | Type    |
|-------------|---------|
| id          | int     |
| name        | varchar |
| department  | varchar |
| managerId   | int     |


### Question

Write a solution to find managers with at least five direct reports.

### Solution

```sql
    with cte1 as (
    select e1.managerID, e1.name, count(e1.id) as reportees_count from Employee e1 inner join Employee e2 on e1.id = e2.managerId group by e2.managerId having reportees_count  >= 5)

    select name from cte1;
```

### Concepts

The query uses `CTE`, `SELF JOIN`, count aggregte function on manager_id column to find reportees of >= 5
