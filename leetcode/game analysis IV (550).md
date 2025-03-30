=======================================================
### 550. Game Play Analysis IV (https://leetcode.com/problems/game-play-analysis-iv/description)
=======================================================

### Table Schema

#### Table: Activity

|---------------|---------|
| Column Name   | Type    |
|---------------|---------|
| player_id     | int     |
| device_id     | int     |
| event_date    | date    |
| games_played  | int     |
|---------------|---------|

### Question

Write a solution to report the fraction of players that logged in again on the day after the day they first logged in, rounded to 2 decimal places. In other words, you need to count the number of players that logged in for at least two consecutive days starting from their first login date, then divide that number by the total number of players.

### Solution

```sql
    SELECT
        ROUND(COUNT(DISTINCT player_id) / (SELECT COUNT(DISTINCT player_id) FROM Activity), 2) AS fraction
        FROM
        Activity
        WHERE
        (player_id, DATE_SUB(event_date, INTERVAL 1 DAY))
        IN (
            SELECT player_id, MIN(event_date) AS first_login FROM Activity GROUP BY player_id
    )
```

### Concepts

The query uses concepts of `SUB QUERIES` and `PERCENTAGE` to get percentage of players logged in for two consecutive days
