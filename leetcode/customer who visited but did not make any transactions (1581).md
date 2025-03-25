
=======================================================
### 1581. Customer who visited byt did not make any transactions (https://leetcode.com/problems/customer-who-visited-but-did-not-make-any-transactions/)
=======================================================

### Table: Employees, EmployeeUNI 

### Table Schema

#### Table: Visits

| Column Name  | Type  |
|-------------|-------|
| visit_id    | int   |
| customer_id | int   |

visit_id is the column with unique values for this table.
This table contains information about the customers who visited the mall.
 

#### Table: Transactions

| Column Name    | Type    |
|----------------|---------|
| transaction_id | int     |
| visit_id       | int     |
| amount         | int     |
|----------------|---------|

transaction_id is column with unique values for this table.
This table contains information about the transactions made during the visit_id.

### Question

Write a solution to find the IDs of the users who visited without making any transactions and the number of times they made these types of visits.

### Solution

```sql
    select vi.customer_id, count(*) as count_no_trans from visits vi left join transactions tr on vi.visit_id = tr.visit_id
    where tr.transaction_id is null group by vi.customer_id order by vi.customer_id;
```

### Concepts

The query uses a `LEFT JOIN` to combine two tables, performed `COUNT` after `FILTERING` for null values
