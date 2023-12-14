# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to find the confirmation rate of each user, which can be calculated by dividing the number of `confirmed` actions by the total number of actions for each user. 

# Approach
<!-- Describe your approach to solving the problem. -->
1. Select specific columns from the table.

    > `SELECT` → This command retrieves data from a database

2. Count the total number of requested confirmation messages.

    > `COUNT()` → This function returns the number of rows

    > `SUM()` → This function returns the total sum of a numeric column

    > `ROUND(number, decimal)` → This function rounds a number to a specified number of decimal places

    > `IFNULL(expression, alt_value)` → This function returns the `alt_value` if the `expression` is `NULL`

    > `AS` → This command renames a column with an alias (temporary name). In most database languages, we can skip the `AS` keyword and get the same result

3. Combine other tables to pair each signup with the corresponding confirmation.

    > `LEFT JOIN` → This command returns all rows from the left table (table 1), and the matching rows from the right table (table 2). The result is `NULL` from the right side, if there is no match.

    > `ON` → This allows to specify the column names for join keys in both tables. It is used to join tables where the column names don’t match in both tables.

4. Group the results based on specific columns to get one row for each user with their corresponding confirmation rate.

    > `GROUP BY` → This command groups rows that have the same values into summary rows, typically to perform aggregate functions on them

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of rows in the table. This is because the query processes each row in the table once to calculate the confirmation rate.

# Code
### Solution 1:
```
SELECT 
    Signups.user_id, 
    IFNULL(ROUND(SUM(action = 'confirmed') / COUNT(*), 2), 0.00) AS confirmation_rate
FROM Signups
LEFT JOIN Confirmations ON Signups.user_id = Confirmations.user_id
GROUP BY Signups.user_id;
```

### Solution 2:
```
SELECT 
    s.user_id,
    CASE 
        WHEN c.time_stamp IS NULL 
        THEN 0.00 
        ELSE ROUND(SUM(action='confirmed')/count(action),2) 
        END AS confirmation_rate
FROM Signups s
LEFT JOIN Confirmations c ON c.user_id=s.user_id
GROUP BY s.user_id
```

### Solution 3:
```
SELECT 
    s.user_id, 
    ROUND(AVG(IF(c.action = "confirmed", 1, 0)),2) AS confirmation_rate 
FROM Signups AS s
LEFT JOIN Confirmations as c ON s.user_id = c.user_id 
GROUP BY user_id;
```
