=======================================================
### 1070. Product Sales Analysis III (https://leetcode.com/problems/product-sales-analysis-iii)
=======================================================

### Table Schema

#### Table: Sales

| Column Name | Type  |
|-------------|-------|
| sale_id     | int   |
| product_id  | int   |
| year        | int   |
| quantity    | int   |
| price       | int   |

#### Table: Product

+--------------+---------+
| Column Name  | Type    |
|--------------|---------|
| product_id   | int     |
| product_name | varchar |

### Question

Write a solution to select the product id, year, quantity, and price for the first year of every product sold.

### Solution

```sql
        with cte1 as 
        ( select product_id, 
                 year as first_year, 
                 rank() over(partition by product_id order by year) as ranking, quantity, price from Sales )

        select product_id, first_year, quantity, price from cte1 where ranking = 1

```

### Concepts

The query uses concept of `CTE` and `WINDOW FUNCTIONS` to extract first time records of products sold
