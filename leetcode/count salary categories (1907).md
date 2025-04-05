=======================================================
### 1907. Count Salary Categories (https://leetcode.com/problems/count-salary-categories/description/)
=======================================================

### Table Schema

#### Table: Accounts

| Column Name | Type |
|-------------|------|
| account_id  | int  |
| income      | int  |

### Question

Write a solution to calculate the number of bank accounts for each salary category. The salary categories are:

"Low Salary": All the salaries strictly less than $20000.
"Average Salary": All the salaries in the inclusive range [$20000, $50000].
"High Salary": All the salaries strictly greater than $50000.
The result table must contain all three categories. If there are no accounts in a category, return 0.

### Solution

```sql
        SELECT 'Low Salary' AS category, 
            COUNT(if(income<20000,1,null)) AS accounts_count
        FROM Accounts
        UNION ALL
        SELECT 'Average Salary', 
            COUNT(if(income>=20000 and income<=50000,1,null))
        FROM Accounts
        UNION ALL
        SELECT 'High Salary', 
            COUNT(if(income>50000,1,null))
        FROM Accounts;
```

### Concepts

The query uses a `UNION ALL` to combine different salay categories based on conditions provided