=======================================================
### 596. Classes more than 5 students (https://leetcode.com/problems/classes-more-than-5-students)
=======================================================

### Table Schema

#### Table: Courses

| Column Name | Type    |
|-------------|---------|
| student     | varchar |
| class       | varchar |


### Question

Write a solution to find all the classes that have at least five students.

### Solution

```sql
    select class from Courses group by class having count(student) >= 5
```

### Concepts

The query uses concept of `GROUP FUNCTION` and `HAVING` to filter on agg/grouped columns
