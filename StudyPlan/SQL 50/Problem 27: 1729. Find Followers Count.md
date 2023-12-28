# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to find the number of followers for each user.

# Approach
<!-- Describe your approach to solving the problem. -->
1. Select specific columns from the table.

    > `SELECT` → This command retrieves data from a database

2. Count the number of followers for each user.

    > `COUNT()` → This function returns the number of rows

    > `AS` → This command renames a column with an alias (temporary name). In most database languages, we can skip the `AS` keyword and get the same result

3. Group and arrange the results based on user id to show the count of followers for each user.

    > `GROUP BY` → This command groups rows that have the same values into summary rows, typically to perform aggregate functions on them

    > `ORDER BY` → This command sorts the result-set in ascending (smallest to largest) order by default

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of rows in the table. This is because the query processes each row in the table once to count the number of followers of each user.

# Code
```
# Write your MySQL query statement below
SELECT user_id, COUNT(follower_id) AS followers_count
FROM Followers
GROUP BY user_id
ORDER BY user_id
```
