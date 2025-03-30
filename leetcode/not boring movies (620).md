=======================================================
### 620. Not Boring Movies (https://leetcode.com/problems/not-boring-movies/description)
=======================================================

### Table Schema

#### Table: Cinema

-----------------------------
| Column Name    | Type     |
-----------------------------
| id             | int      |
| movie          | varchar  |
| description    | varchar  |
| rating         | float    |
-----------------------------

### Question

Write a solution to report the movies with an odd-numbered ID and a description that is not "boring".

### Solution

```sql
    select id, movie, description, rating from cinema
    where id %2 !=0 and description != 'boring'
    order by rating desc
```

### Concepts

The query uses `FILTER` based on given condition and `ORDER` based on rating
