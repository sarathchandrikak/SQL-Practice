=======================================================
### 1341. Movie Rating (https://leetcode.com/problems/movie-rating/description/)
=======================================================

### Table Schema

#### Table: Movies

| Column Name | Type    |
|-------------|---------|
| movie_id    | int     |
| title       | varchar |

#### Table: Users

| Column Name | Type    |
|-------------|---------|
| user_id     | int     |
| name        | varchar |

#### Table: MovieRating

| Column Name | Type    |
|-------------|---------|
| movie_id    | int     |
| user_id     | int     |
| rating      | int     |
| created_at  | date    |

### Question

Find the name of the user who has rated the greatest number of movies. In case of a tie, return the lexicographically smaller user name.
Find the movie name with the highest average rating in February 2020. In case of a tie, return the lexicographically smaller movie name.

### Solution

```sql
    (SELECT name AS results
        FROM MovieRating JOIN Users USING(user_id)
        GROUP BY name
        ORDER BY COUNT(*) DESC, name
        LIMIT 1)

        UNION ALL

    (SELECT title AS results
        FROM MovieRating JOIN Movies USING(movie_id)
        WHERE EXTRACT(YEAR_MONTH FROM created_at) = 202002
        GROUP BY title
        ORDER BY AVG(rating) DESC, title
        LIMIT 1);
```

### Concepts

This query uses UNION ALL to combine username, title based on given conditions