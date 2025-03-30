=======================================================
### 1211. Queries Quality and Percentage (https://leetcode.com/problems/queries-quality-and-percentage/description)
=======================================================

### Table Schema

#### Table: Delivery

|-----------------------------|---------|
| Column Name                 | Type    |
|-----------------------------|---------|
| delivery_id                 | int     |
| customer_id                 | int     |
| order_date                  | date    |
| customer_pref_delivery_date | date    |
|-----------------------------|---------|

### Question

Write a solution to find the percentage of immediate orders in the first orders of all customers, rounded to 2 decimal places.

### Solution

```sql
    Select 
    round(avg(order_date = customer_pref_delivery_date)*100, 2) as immediate_percentage
    from Delivery
    where (customer_id, order_date) in (
        Select customer_id, min(order_date) 
        from Delivery
        group by customer_id
    )
```

### Concepts

The query uses concepts of `SUB QUERIES` and `AGG FUNC` to find percentage of immediate orders
