=======================================================
### 1683. Invalid Tweets (https://leetcode.com/problems/invalid-tweets/description/)
=======================================================

### Table: Tweets

### Table Schema 

| Column Name | Type    |
|-------------|---------|
| tweet_id    | int     |
| content     | varchar |

### Question
Write a solution to find the IDs of the invalid tweets. The tweet is invalid if the number of characters used in the content of the tweet is strictly greater than 15.

### Solution

```sql
      select tweet_id from Tweets where length(content) > 15
```

### Concepts

The query applies the concepts of **SELECT**, **FROM**, and **WHERE** to retrieve the `tweet_id` from the `Tweets` table where the `content` length exceeds 15 characters.
