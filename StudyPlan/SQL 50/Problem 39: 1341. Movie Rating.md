# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to find the name of the user who has rated the greatest number of movies and the movie name with the highest average rating in February 2020. In case of a tie, we should return lexicographically smaller user and movie name.

# Approach
<!-- Describe your approach to solving the problem. -->
1. Find the user who has rated the most movies.

    > `SELECT` → This command retrieves data from a database

    > `AS` → This command renames a column with an alias (temporary name). In most database languages, we can skip the `AS` keyword and get the same result

    > `WHERE` → This command filters a result set to include only records that fulfill a specified condition

    > `=` → This operator compares if one value is equal to another value

    > `GROUP BY` → This command groups rows that have the same values into summary rows, typically to perform aggregate functions on them

    > `ORDER BY` → This command sorts the result-set in ascending (smallest to largest) order by default

    > `COUNT()` → This function returns the number of rows

    > `DESC` → This keyword sorts the records in descending (largest to smallest) order

    > `LIMIT` → This clause specifies the number of records to return

2. Find the movie with the highest average rating in February 2020.

    > `AND` → This operator filters records based on more than one condition

    > `LIKE` → This operator searches for a specified pattern in a column

    > `AVG()` → This function returns the average value of an expression

3. Combine the result sets into a single result set without removing duplicate rows.

    > `UNION ALL` → This operator combines the result-set of two or more `SELECT` statements (every `SELECT` statement must have the same number/data type/order of columns). It returns all rows from the query and it does not remove duplicate rows between the various `SELECT` statements

# Complexity
- Time complexity: $O(nlogn)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of rows in the table. This is because the query involves joining tables, which requires scanning through all the rows in the tables to check the conditions.

# Code
```
(
    SELECT u.name AS results
    FROM MovieRating mr, Users u
    WHERE mr.user_id = u.user_id
    GROUP BY mr.user_id
    ORDER BY COUNT(1) DESC, u.name
    LIMIT 1
)
UNION ALL
(
    SELECT m.title AS results
    FROM MovieRating mr, Movies m 
    WHERE mr.movie_id = m.movie_id AND mr.created_at LIKE '2020-02%'
    GROUP BY mr.movie_id
    ORDER BY AVG(rating) DESC, m.title
    LIMIT 1
)
```
