=======================================================
### 1068. Product Sales Analysis I (https://leetcode.com/problems/product-sales-analysis-i/description/)
=======================================================

### Tables: Sales, Product

### Table Schema - Sales

| Column Name | Type |
|-------------|------|
| sale_id     | int  |
| product_id  | int  |
| year        | int  |
| quantity    | int  |
| price       | int  |


### Table Schema - Product

| Column Name  | Type    |
|--------------|---------|
| product_id   | int     |
| product_name | varchar |


### Question

Write a solution to report the product_name, year, and price for each sale_id in the Sales table.

### Solution

  ```sql
        with sale_cte as (
            select s.sale_id, s.product_id, p.product_name, s.year, s.price from 
            Sales s inner join Product p on s.product_id = p.product_id group by s.sale_id)

        select product_name, year, price from sale_cte ;
  ```

### Concepts

The query uses a **Common Table Expression (CTE)** to simplify complex queries by creating a temporary result set (`sale_cte`). 
It performs an **INNER JOIN** between the `Sales` and `Product` tables based on `product_id`, and uses **GROUP BY** on `sale_id` to aggregate the data. 
Finally, the main query selects specific columns (`product_name`, `year`, `price`) from the CTE.
