# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to find the person who has the most friends and the number of friends they have.

# Approach
<!-- Describe your approach to solving the problem. -->
1. Combine two columns into one list to find all people who either sent or received friend requests.

    > `SELECT` → This command retrieves data from a database

    > `AS` → This command renames a column with an alias (temporary name). In most database languages, we can skip the `AS` keyword and get the same result

    > `UNION ALL` → This operator combines the result-set of two or more `SELECT` statements (every `SELECT` statement must have the same number/data type/order of columns). It returns all rows from the query and it does not remove duplicate rows between the various `SELECT` statements

2. Calculate the number of friends each person has. 

    > `COUNT()` → This function returns the number of rows

    > Asterisk (`*`) → This symbol specifies that the query should return all columns of the queried tables

3. Group the results to show all records related to the same person.

    > `GROUP BY` → This command groups rows that have the same values into summary rows, typically to perform aggregate functions on them

4. Arrange the results by the number of friends in descending order. 

    > `ORDER BY` → This command sorts the result-set in ascending (smallest to largest) order by default

    > `DESC` → This keyword sorts the records in descending (largest to smallest) order

5. Show the person with the most friends.

    > `LIMIT` → This clause specifies the number of records to return

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of rows in the table. The query processes all the rows in the table to count the number of friends for each person.

# Code
```
SELECT id, COUNT(*) AS num 
FROM (
    SELECT requester_id AS id FROM RequestAccepted
    UNION ALL
    SELECT accepter_id FROM RequestAccepted
) AS friends_count
GROUP BY id
ORDER BY num DESC 
LIMIT 1;
```
