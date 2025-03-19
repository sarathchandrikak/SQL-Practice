
=======================================================
### 1378. Replace Employee ID With The Unique Identifier (https://leetcode.com/problems/replace-employee-id-with-the-unique-identifier/description/)
=======================================================

### Table: Employees, EmployeeUNI 

### Table Schema

#### Employees

| Column Name | Type    |
|-------------|---------|
| id          | int     |
| name        | varchar |

#### EmployeeUNI

| Column Name | Type |
|-------------|------|
| id          | int  |
| unique_id   | int  |

### Question

Write a solution to show the unique ID of each user, If a user does not have a unique ID replace just show null.


### Solution

```sql
    select coalesce(eun.unique_id, null) as unique_id, e.name from EmployeeUNI eun right join Employees e on eun.id = e.id;
```

### Concepts

The query uses a `RIGHT JOIN` to combine two tables, ensuring all records from the right table are returned. It also employs the `COALESCE` function to handle `NULL` values.
