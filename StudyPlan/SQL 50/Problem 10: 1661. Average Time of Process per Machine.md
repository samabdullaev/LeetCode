# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to calculate the average time each machine takes to complete a process. For this, we can find find the time taken for each process on a machine and then calculate the average time for each machine.

# Approach
<!-- Describe your approach to solving the problem. -->
1. Select specific columns from the table.
    > `SELECT` → This command retrieves data from a database

    > `AS` → This command renames a column with an alias (temporary name). In most database languages, we can skip the `AS` keyword and get the same result

2. Count the number of unique processes that were run on each machine.
    > `COUNT()` → This function returns the number of rows

    > `DISTINCT` → This statement returns only distinct (different) values

3. Calculate the total time it takes to complete each process on a machine and round this to the specified number of decimal places. 

    > `ROUND(number, decimal)`  → This function rounds a `number` to a specified number of `decimal` places

    > `SUM()` → This function returns the total sum of a numeric column

    > `IF(condition, value_if_true, value_if_false)` → This function returns a value if a `condition` is `TRUE`, or another value if it is `FALSE`
    By negating the `start` time, we ensure that we get the accurate duration of the process on a machine (it subtracts the `start` time from the `end` time).

4. Group and arrange the results based on specific columns.

    > `GROUP BY` → This command groups rows that have the same values into summary rows, typically to perform aggregate functions on them

    > `ORDER BY` → This command sorts the result-set in ascending (smallest to largest) order

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of rows in the table. The query needs to examine each row to calculate the average processing time for each machine.

# Code
```
SELECT 
    machine_id, 
    ROUND(SUM(IF(activity_type='start', -timestamp, timestamp)) / COUNT(DISTINCT process_id), 3) AS processing_time
FROM Activity
GROUP BY machine_id
ORDER BY machine_id
```
