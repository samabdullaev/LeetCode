# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to find users with valid email addresses.

A valid e-mail has a prefix name and a domain where:

- `prefix name` → a string that must start with a letter and may contain upper/lower case letters, digits, underscore '`_`', period '`.`', and/or dash '`-`' 
- `domain`  → '@leetcode.com'

# Approach
<!-- Describe your approach to solving the problem. -->
1. Select specific columns from the table.

    > `SELECT` → This command retrieves data from a database

    > Asterisk (`*`) → This symbol specifies that the query should return all columns of the queried tables

2. Filter the valid email addresses from the table.

    > `WHERE` → This command filters a result set to include only records that fulfill a specified condition

    > `REGEXP` → This performs a pattern match of a string expression against a pattern

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of rows in the table. This is because the query scans each row in the table to find users with valid email addresses.

# Code
```
SELECT *
FROM users
WHERE mail REGEXP '^[a-zA-Z][a-zAZ0-9_.-]*@leetcode[.]com
```
