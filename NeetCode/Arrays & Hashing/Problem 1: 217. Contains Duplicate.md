# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
Given an array of numbers, we need to check if any value repeats:

- return `True`→ if any value contains duplicates

- return `False`→ if every value is distinct

##### Good to know:

1. `Array`→ a data structure that serves as a container for storing an ordered collection of elements, typically of the same data type, allowing for efficient access to individual elements by their index

2. `Duplicate`→ a value that appears **more than once** in the given array

3. `Distinct`→ a value that appears **only once** in the given array

# Approach
<!-- Describe your approach to solving the problem. -->
1. Create an empty set to store unique elements

    ```
    hashset = set()
    ```

2. Go through every value in the input array

    ```
    for n in nums:
        # code to be executed
    ```

3. Check if the current element is already in the hashset.
    - If it is, return `True` (as it indicates a duplicate)

        ```
        if n in hashset:
            return True
        ```
    - If it's not, add the element to the hashset

        ```
        hashset.add(n)
        ```

4. If the loop completes without finding any duplicates, return `False`

    ```
    return False
    ```

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of elements in the input array. This is because, in the worst-case scenario, we scan through the list of inputs once.

- Space complexity: $O(n)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
`n` is the number of elements in the input array. This is because, in the worst-case scenario, the hashset may contain all elements of the input array.

# Code
```
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        hashset = set()

        for n in nums:
            if n in hashset:
                return True
            hashset.add(n)
        return False
```
