=======================================================
### 1280. Find Customer Referee (https://leetcode.com/problems/students-and-examinations/description/)
=======================================================

### Table Schema

#### Table: Students

---------------------------
| Column Name   | Type    |
---------------------------
| student_id    | int     |
| student_name  | varchar |
---------------------------
 

#### Table: Subjects

--------------------------
| Column Name  | Type    |
--------------------------
| subject_name | varchar |
--------------------------
 

#### Table: Examinations

--------------------------
| Column Name  | Type    |
--------------------------
| student_id   | int     |
| subject_name | varchar |
--------------------------

### Question

Write a solution to find the number of times each student attended each exam.

### Solution

```sql
    select s.student_id, s.student_name, su.subject_name, count(e.student_id) as attended_exams from Students s cross join Subjects su
    left join Examinations e 
    on e.student_id = s.student_id and e.subject_name = su.subject_name group by s.student_id, s.student_name, su.subject_name
    order by s.student_id, s.student_name, su.subject_name
```

### Concepts

The query uses multiple `JOINS` and count from exams table to get count of only attended exams