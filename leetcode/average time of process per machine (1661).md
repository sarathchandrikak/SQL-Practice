=======================================================
### 1661. Average Time of Process per Machine (https://leetcode.com/problems/average-time-of-process-per-machine/description)
=======================================================

### Table Schema

#### Table: Activity

|----------------|---------|
| Column Name    | Type    |
|----------------|---------|
| machine_id     | int     |
| process_id     | int     |
| activity_type  | enum    |
| timestamp      | float   |
|----------------|---------|


### Question

Average time of process per machine

### Solution

```sql
        with s3 as (

        with s1 as
        (select machine_id, process_id, activity_type, timestamp
        from activity where activity_type = 'start'),
        s2 as 
        (select machine_id, process_id, activity_type, timestamp
        from activity where activity_type = 'end')

        select s1.machine_id, s1.process_id, s2.timestamp - s1.timestamp as processing_time from s1 inner join
        s2 on s1.machine_id = s2.machine_id and s1.process_id = s2.process_id)

        select machine_id, round(avg(processing_time),3) as processing_time from s3 
        group by machine_id 
```

### Concepts

The query is constructed using multiple `CTEs` based on activity time calculate average of processing time