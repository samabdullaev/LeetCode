# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to find the IDs of tweets with content exceeding 15 characters.

# Approach
<!-- Describe your approach to solving the problem. -->
1. Select specific columns from the table.

    > `SELECT` → This command retrieves data from a database

2. Filter for tweets with content that is longer than 15 characters.

    > `WHERE` → This command filters a result set to include only records that fulfill a specified condition

    > `LENGTH()` → This function returns the length of a string (in bytes)

    > `>` → This operator compares if one value is greater than another value

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of rows in the table. In the worst case, it would need to examine each row to check the content length.

# Code
```
SELECT tweet_id FROM Tweets WHERE LENGTH(content)>15
```
