=======================================================
### 1757. Recyclable and Low Fat Products
=======================================================

### Table - Products

### Table Schema
  
| Column Name | Type   |
|-------------|--------|
| product_id  | int    |
| low_fats    | enum   |
| recyclable  | enum   |

### Question
Write a solution to find the ids of products that are both low fat and recyclable.
INFO - 
    
product_id is the primary key (column with unique values) for this table.
low_fats is an ENUM (category) of type ('Y', 'N') where 'Y' means this product is low fat and 'N' means it is not.
recyclable is an ENUM (category) of types ('Y', 'N') where 'Y' means this product is recyclable and 'N' means it is not.

``` sql
    select product_id from products where low_fats='Y' and recyclable ='Y'
```

### Concepts

Select, filter operation using where condition
