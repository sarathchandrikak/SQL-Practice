=======================================================
### 1251. Average Selling Price (https://leetcode.com/problems/average-selling-price/description)
=======================================================

### Table Schema

#### Table: Prices

#### Table: Products

| Column Name | Type  |
|-------------|-------|
| product_id  | int   |
| start_date  | date  |
| end_date    | date  |
| price       | int   |

#### Table: UnitsSold

| Column Name   | Type  |
|--------------|-------|
| product_id   | int   |
| purchase_date| date  |
| units        | int   |

### Question

Write a solution to find the average selling price for each product. average_price should be rounded to 2 decimal places. If a product does not have any sold units, its average selling price is assumed to be 0.

### Solution

```sql
    WITH cte1 AS (
    SELECT 
        p.product_id, 
        COALESCE(u.units, 0) AS units, 
        COALESCE(p.price * u.units, 0) AS sp
    FROM Prices p
    LEFT JOIN UnitsSold u ON p.product_id = u.product_id 
    AND u.purchase_date >= p.start_date 
    AND u.purchase_date <= p.end_date
    )
    select product_id, COALESCE(round(sum(sp)/sum(units),2),0) as average_price from cte1 group by product_id
```

### Concepts

The query uses concepts of `CTE` and `COALESCE` and to find out price of total number of units sold
