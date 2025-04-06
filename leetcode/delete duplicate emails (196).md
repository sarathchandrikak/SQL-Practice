=======================================================
### 196. Delete Duplicate Emails (https://leetcode.com/problems/patients-with-a-condition/)
=======================================================

### Table Schema

#### Table: Patients

| Column Name  | Type    |
|--------------|---------|
| patient_id   | int     |
| patient_name | varchar |
| conditions   | varchar |

### Question

Write a solution to find the patient_id, patient_name, and conditions of the patients who have Type I Diabetes. Type I Diabetes always starts with DIAB1 prefix.

### Solution

```sql
        select patient_id, patient_name, conditions from Patients where conditions like '% DIAB1%' or conditions like 'DIAB1%'
```

### Concepts

The query uses `LIKE FUNCTION` to filter on the starting or ending of string