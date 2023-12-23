# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to find the percentage of players that logged in for at least 2 consecutive days starting from their first login date.

# Approach
<!-- Describe your approach to solving the problem. -->
1. Find the earliest login date for each player.

    > `MIN()` → This function returns the smallest value of the selected column

    > `GROUP BY` → This command groups rows that have the same values into summary rows, typically to perform aggregate functions on them

2. Combine the table to check if a player logged in on the day after their first login.

    > `JOIN` / `INNER JOIN` → These commands return records that have matching values in both tables

    > `ON` → This allows to specify the column names for join keys in both tables. It is used to join tables where the column names don’t match in both tables.

    > `AND` → This operator filters records based on more than one condition

    > `DATEDIFF(date1, date2)` → This function returns the number of days between two date values

3. Count the distinct players who meet the above criteria.

    > `SELECT` → This command retrieves data from a database

    > `COUNT()` → This function returns the number of rows

    > `DISTINCT` → This statement returns only distinct (different) values

4. Calculate the percentage of those players among all players.

    > `ROUND(number, decimal)` → This function rounds a `number` to a specified number of `decimal` places

    > `AS` → This command renames a column with an alias (temporary name). In most database languages, we can skip the `AS` keyword and get the same result

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of rows in the table. The query needs to examine each row to find the first login date for each player and then join and filter the data to count players who logged in on consecutive days.

# Code
```
SELECT ROUND(
    (SELECT COUNT(DISTINCT a.player_id) FROM Activity a
    INNER JOIN (
        SELECT player_id, MIN(event_date) AS first_logged 
        FROM Activity 
        GROUP BY player_id
    ) b ON DATEDIFF(a.event_date, b.first_logged)=1 AND a.player_id = b.player_id)
    /
(SELECT COUNT(DISTINCT player_id) FROM Activity),2) AS fraction;
```
