
## 🔥 SQL Questions Using `CASE` Statements

### **1. Tiered Discount Calculation** 

#### 📌 Problem:
Calculate the discounted total for each customer based on how much they've spent.
Apply discount tiers:
- ≥ 5000 → 20%
- ≥ 3000 → 15%
- ≥ 1000 → 10%
- < 1000 → no discount


#### 🧱 Table Schema:
**Table:** `customer_purchases`

| Column Name     | Data Type        |
|-----------------|------------------|
| `customer_id`   | `INT`            |
| `customer_name` | `VARCHAR(100)`   |
| `total_spent`   | `DECIMAL(10,2)`  |

#### 💡 Solution


```sql
    SELECT 
        customer_id,
        customer_name,
        total_spent,
        CASE
            WHEN total_spent >= 5000 THEN total_spent * 0.80
            WHEN total_spent >= 3000 THEN total_spent * 0.85
            WHEN total_spent >= 1000 THEN total_spent * 0.90
            ELSE total_spent
        END AS discounted_total
    FROM customer_purchases;
```

---

### **2. Calculate Gender-Wise Average Salary**

#### 📌 Problem:
Return overall average salary, average salary for male employees, and female employees.

#### 🧱 Table Schema:
**Table:** `employees`

| Column Name     | Data Typ         |
|-----------------|------------------|
| `employee_id`   | `INT`            |
| `gender`        | `CHAR(1)`        |
| `salary`        | `DECIMAL(10,2)`  |

#### 💡 Solution

```sql
    SELECT 
        AVG(salary) AS overall_avg_salary,
        AVG(CASE WHEN gender = 'M' THEN salary END) AS avg_male_salary,
        AVG(CASE WHEN gender = 'F' THEN salary END) AS avg_female_salary
    FROM employees;
```
---

### **3. Compare Current Sale to Previous Sale**

#### 📌 Problem:
For each customer, show their sales along with a column sale_trend that says:

'Increased' if current sale > previous
'Decreased' if current sale < previous
'Same' if equal
'First Sale' if there’s no previous

#### 🧱 Table Schema:
**Table:** `sales`

| Column Name     | Data Type        |
|-----------------|------------------|
| `sale_id`       | `INT`            |
| `customer_id`   | `INT`            |
| `sale_date`     | `DATE`           |
| `amount`        | `DECIMAL(10,2)`  |

#### 💡 Solution

```sql
      SELECT 
          customer_id,
          sale_id,
          sale_date,
          amount,
          CASE 
              WHEN LAG(amount) OVER (PARTITION BY customer_id ORDER BY sale_date) IS NULL THEN 'First Sale'
              WHEN amount > LAG(amount) OVER (PARTITION BY customer_id ORDER BY sale_date) THEN 'Increased'
              WHEN amount < LAG(amount) OVER (PARTITION BY customer_id ORDER BY sale_date) THEN 'Decreased'
              ELSE 'Same'
          END AS sale_trend
      FROM sales;
```
---

### **4. Flip Gender Values in a Table**

#### 📌 Problem:
Write a query to return all users, but flip their gender:

'M' becomes 'F'
'F' becomes 'M'

#### 🧱 Table Schema:
**Table:** `users`

| Column Name  | Data Type      |
|--------------|----------------|
| `user_id`    | `INT`          |
| `name`       | `VARCHAR(100)` |
| `gender`     | `VARCHAR(1)`   |

#### 💡 Solution:

```sql
      SELECT 
          user_id,
          name,
          gender,
          CASE 
              WHEN gender = 'M' THEN 'F'
              WHEN gender = 'F' THEN 'M'
              ELSE 'Unknown'
          END AS flipped_gender
      FROM users;
```
---

### **5. Time Between Events Based on Type**

#### 📌 Problem:
For each user and each event_type, calculate the time (in hours) since their last event of the same type.

#### 🧱 Table Schema:
**Table:** `events`

| Column Name     | Data Type       |
|-----------------|-----------------|
| `event_id`      | `INT`           |
| `user_id`       | `INT`           |
| `event_type`    | `VARCHAR(50)`   |
| `event_time`    | `TIMESTAMP`     |

#### 💡 Solution 

```sql
      SELECT 
          user_id,
          event_id,
          event_type,
          event_time,
          EXTRACT(EPOCH FROM (event_time - 
              LAG(event_time) OVER (PARTITION BY user_id, event_type ORDER BY event_time)))/3600 
              AS hours_since_last
      FROM user_events;
```
---

Additional Reference - https://www.stratascratch.com/blog/a-comprehensive-guide-to-case-when-statements-in-sql/


