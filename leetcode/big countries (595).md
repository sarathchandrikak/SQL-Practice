=======================================================
### 595. Big Countries (https://leetcode.com/problems/big-countries/description/)
=======================================================

### Table - World
### Table Schema

| Column Name | Type    |
|-------------|---------|
| name        | varchar |
| continent   | varchar |
| area        | int     |
| population  | int     |
| gdp         | bigint  |

### Question
A country is big if:

it has an area of at least three million (i.e., 3000000 km2), or
it has a population of at least twenty-five million (i.e., 25000000).
Write a solution to find the name, population, and area of the big countries.

### Solution

```sql
   select name, population, area from World where area >= 3000000 or population >= 25000000;
```

### Concepts

Select, filter using where condition
