=======================================================
### 1978. Employees whose manager left the company (https://leetcode.com/problems/employees-whose-manager-left-the-company/description/)
=======================================================

### Table Schema

#### Table: Employees

| Column Name | Type     |
|-------------|----------|
| employee_id | int      |
| name        | varchar  |
| manager_id  | int      |
| salary      | int      |

### Question

Find the IDs of the employees whose salary is strictly less than $30000 and whose manager left the company. When a manager leaves the company, their information is deleted from the Employees table, but the reports still have their manager_id set to the manager that left.

### Solution

```sql
    select employee_id from Employees where manager_id not in (select employee_id from Employees) and salary < 30000 order by employee_id
```

### Concepts

The query is achieved by using `SUBQUERY` and applying `FILTER` based on given condition of < 30000
