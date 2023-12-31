# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
Pre-defined terms:

1. `Multi-dimensional array` → a recursive data structure that contains integers or other multi-dimensional arrays

2. `Flattened array` → a version of that array with some or all of the sub-arrays removed and replaced with the actual elements in that sub-array

We need to return a flattened version of the given multi-dimensional array.

# Approach
<!-- Describe your approach to solving the problem. -->
1. These are comment delimiters for a multi-line comment to help explain and document code while preventing ignored text from executing. These comments are commonly used in formal documentation for better code understanding.

    ```
    /**
    * Multi-line comment
    */
    ```

2. This is a special type of comment called a JSDoc comment that explains that the function should take parameters named `arr` and `depth`, which are expected to be an `Array` and a `number`.

    ```
    @param {Array} arr
    @param {number} depth
    ```

3. This is a special type of comment called a JSDoc comment that explains what the code should return, which, in this case, is an `Array`. It helps developers and tools like code editors and documentation generators know what the function is supposed to produce.

    ```
    @return {Array}
    ```

4. This is how we define a function named `flat` that takes an array `arr` and a number `n` as its arguments.

    ```
    var flat = function (arr, n) {
        // code to be executed
    };
    ```

5. This `flat` method flattens the array `arr` up to depth `n`.

    ```
    return arr.flat(n)
    ```

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the total number of elements in the input array. This is because the code needs to iterate over each element in the array.

- Space complexity: $O(n)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
`n` is the total number of elements in the input array. This is because the function creates a new array with all the elements from the sub-arrays, so the space required is proportional to the number of elements in the input array.

# Code
```
/**
 * @param {Array} arr
 * @param {number} depth
 * @return {Array}
 */
var flat = function (arr, n) {
    return arr.flat(n)
};
```
