=======================================================
### 2356. Number of Unique Subjects Taught by Each Teacher (https://leetcode.com/problems/number-of-unique-subjects-taught-by-each-teacher)
=======================================================

### Table Schema

#### Table: Teacher

| Column Name | Type |
|-------------|------|
| teacher_id  | int  |
| subject_id  | int  |
| dept_id     | int  |

### Question

Write a solution to calculate the number of unique subjects each teacher teaches in the university.

### Solution

```sql
    select teacher_id, count(DISTINCT subject_id) as cnt from Teacher group by teacher_id
```

### Concepts

The query uses concept of `COUNT FUNCTION` to find unique subjects of teachers
