# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to capitalize the first character of each name and convert the rest of the characters to lowercase.

# Approach
<!-- Describe your approach to solving the problem. -->
1. Select specific columns from the table.

    > `SELECT` → This command retrieves data from a database

    > `AS` → This command renames a column with an alias (temporary name). In most database languages, we can skip the `AS` keyword and get the same result

2. Capitalize the first character of the name.

    > `UPPER()` → This function converts a string to upper-case

    Use either of this to extract a specified number of characters from the left side of the `name` string:

    - `LEFT(string, number_of_chars)` → This function extracts a `number_of_chars` from a `string` (starting from left)

    - `SUBSTRING(string, start, length)` → This function extracts the `length` number of characters from a `string` from the `start` position

3. Convert the remaining characters to lowercase.

    > `LOWER()` → This function converts a string to lower-case

    > `SUBSTRING(string, start)` → This function extracts a substring from a `string` from the `start` position

4. Combine the capitalized first character with the lowercase rest.

    > `CONCAT()` → This function adds two or more expressions together

5. Order the result by `user_id`.

    > `ORDER BY` → This command sorts the result-set in ascending (smallest to largest) order by default

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of rows in the table. This is because the query processes each row in the table to perform the string operations and order them.

# Code
### Solution 1:
```
SELECT 
    user_id, 
    CONCAT(UPPER(LEFT(name,1)),LOWER(SUBSTRING(name,2))) AS name
FROM Users 
ORDER BY user_id
```

### Solution 2:
```
SELECT 
    user_id,
    CONCAT(UPPER(SUBSTRING(name, 1, 1)), LOWER(SUBSTRING(name, 2))) AS name
FROM Users
ORDER BY user_id
```
