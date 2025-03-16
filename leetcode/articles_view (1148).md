
=======================================================

### 1148. Article Views I (https://leetcode.com/problems/article-views-i/description/)
=======================================================


### Table: Views

### Table Schema

| Column Name | Type   |
|-------------|--------|
| article_id  | int    |
| author_id   | int    |
| viewer_id   | int    |
| view_date   | date   |

### Question

Write a solution to find all the authors that viewed at least one of their own articles.


### Solution

```sql
    select author_id as id from Views where author_id = viewer_id group by author_id having count(viewer_id) >= 1 order by id;
```

### Concepts

Here’s a refined version of your statement:

### Concepts

The following concepts are used in the query:
- **Select**: Choosing specific columns or data from a table.
- **Filter**: Applying conditions to restrict the rows returned.
- **Grouping**: Grouping rows based on one or more columns, typically using `GROUP BY`.
- **Filtering on Grouped Data**: Applying conditions on grouped data using `HAVING`.
- **Order By**: Sorting the result set based on one or more columns.

These are the key concepts involved in crafting and executing the query. 

Also this can give an overview of order of keywords of SQL query 

The proper order of SQL keywords is: **SELECT** → **FROM** → **WHERE** → **GROUP BY** → **HAVING** → **ORDER BY**.
