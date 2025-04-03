=======================================================
### 610. Triangle Judgement (https://leetcode.com/problems/triangle-judgement/description)
=======================================================

### Table Schema

#### Table: Triangle
| Column Name | Type |
|-------------|------|
| x           | int  |
| y           | int  |
| z           | int  |

### Question

Report for every three line segments whether they can form a triangle.

### Solution

```sql
    with tri1 as (
    select x, y, z,
        CASE  when x+y > z THEN 1 ELSE 0 END +
        CASE when y+z > x THEN 1 ELSE 0 END +
        CASE when z+x > y THEN 1 ELSE 0 END
        as counter
    from Triangle 
    )

    select x, y, z, 
        CASE 
            when (counter) = 3 then 'Yes' else 'No' 
        END as triangle
    from tri1 
    group by x,y,z
```

### Concepts

The query uses concepts of `CTE, CASE STATEMENTs` to find valid triangles in the column