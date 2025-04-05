=======================================================
### 1164. Product Price at a Given Date (https://leetcode.com/problems/product-price-at-a-given-date/description/)
=======================================================

### Table Schema

#### Table: Products

| Column Name   | Type    |
|-------------  |---------|
| product_id    | int     |
| new_price     | int     |
| change_date   | date    |


### Question

Write a solution to find the prices of all products on 2019-08-16. Assume the price of all products before any change is 10.
 
### Solution

```sql
    WITH cte1 AS (
        SELECT 
            product_id, 
            new_price as price, 
            change_date,
            ROW_NUMBER() OVER (PARTITION BY product_id ORDER BY change_date DESC) AS row_num
        FROM Products
        WHERE change_date <= '2019-08-16'
    )

    SELECT product_id, price from cte1 where row_num=1
    UNION
    select product_id, 10 as price from products 
    where product_id not in (select product_id from cte1)
```

### Concepts

The query uses a `WINDOW` function to find prices of all products based on date column and `UNION` with default value if any value is missed from the filter condition
