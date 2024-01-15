# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to delete all duplicate emails while keeping the one with the smallest ID.

# Approach
<!-- Describe your approach to solving the problem. -->
1. Delete specific rows from the table.

    > `DELETE` → This statement deletes existing records in a table

2. Check if there is a duplicate email with a smaller ID.

    > `WHERE` → This command filters a result set to include only records that fulfill a specified condition

    > `=` → This operator compares if one value is equal to another value

    > `AND` → This operator filters records based on more than one condition

    > `>` → This operator compares if one value is greater than another value

# Complexity
- Time complexity: $O(n^2)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of rows in the table. This is because the query compares each row with every other row in the table to find matching email addresses and delete the row with the higher Id.

# Code
```
DELETE p1
FROM Person p1, Person p2
WHERE p1.Email = p2.Email AND p1.Id > p2.Id;
```
