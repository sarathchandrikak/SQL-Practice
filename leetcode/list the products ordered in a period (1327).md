=======================================================
### 1327. List the products ordered in a period (https://leetcode.com/problems/list-the-products-ordered-in-a-period/description/)
=======================================================

### Table Schema

#### Table: Products

| Column Name      | Type    |
|------------------|---------|
| product_id       | int     |
| product_name     | varchar |
| product_category | varchar |

#### Table: Orders

| Column Name   | Type    |
|---------------|---------|
| product_id    | int     |
| order_date    | date    |
| unit          | int     |

### Question

Write a solution to get the names of products that have at least 100 units ordered in February 2020 and their amount

### Solution

```sql
        with agg_order_data as (
        select product_id, extract(month from order_date) as month, extract(year from order_date) as year, sum(unit) as units_sum from orders group by product_id, month, year
    )
    select p.product_name, a.units_sum as unit  from products p inner join agg_order_data a 
    on p.product_id = a.product_id where a.month = 2 and a.year = 2020 and a.units_sum >= 100
```

### Concepts

The query is achieved by `CTEs`, `FILTER` operations to get the names of products that have 100 units