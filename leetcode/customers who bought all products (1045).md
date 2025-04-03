=======================================================
### 1045. Customers Who Bought All Products (https://leetcode.com/problems/customer-who-bought-all-products/description)
=======================================================

### Table Schema

#### Table: Customer

| Column Name | Type    |
|-------------|---------|
| customer_id | int     |
| product_key | int     |
 

#### Table: Product

| Column Name | Type    |
|-------------|---------|
| product_key | int     |

### Question

Write a solution to report the customer ids from the Customer table that bought all the products in the Product table.

### Solution

```sql
    with cte1 as (
    select customer_id, count(distinct product_key) as dis_prd from Customer group by customer_id
    )

    select customer_id from cte1 where dis_prd = (select count(distinct product_key) from Product)
```

### Concepts

The query uses concepts of `CTE` and `COUNT` Aggregate funcs to find customers who bought all products in product table