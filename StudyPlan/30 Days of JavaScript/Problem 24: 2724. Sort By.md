# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to return a sorted array, where the sorting is based on the output of a given function, which exclusively returns numbers, ensuring the sorted array is in ascending order according to the function's output.

# Approach
<!-- Describe your approach to solving the problem. -->
1. These are comment delimiters for a multi-line comment to help explain and document code while preventing ignored text from executing. These comments are commonly used in formal documentation for better code understanding.

    ```
    /**
    * Multi-line comment
    */
    ```

2. This is a special type of comment called a JSDoc comment that explains that the function should take parameters named `arr` and `fn`, which are expected to be an `Array` and a `Function`.

    ```
    @param {Array} arr
    @param {Function} fn
    ```

3. This is a special type of comment called a JSDoc comment that explains what the code should return, which, in this case, is an `Array`. It helps developers and tools like code editors and documentation generators know what the function is supposed to produce.

    ```
    @return {Array}
    ```

4. This is how we define a function named `sortBy` that takes an array `arr` and a function `fn` as its arguments.

    ```
    var sortBy = function(arr, fn) {
        // code to be executed
    };
    ```

5. This function returns the array sorted in ascending order, where the sorting is determined by the output of the function `fn` applied to each element (`a` and `b`).

    ```
    return arr.sort((a, b) => fn(a) - fn(b));
    ```

# Complexity
- Time complexity: $O(n log n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the length of the input array. This is because the function uses the `sort` method, which has a time complexity of $O(n log n)$ in the average case.

- Space complexity: $O(1)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
This is because the function does not use any additional data structures that grow with the size of the input array.

# Code
```
/**
 * @param {Array} arr
 * @param {Function} fn
 * @return {Array}
 */
var sortBy = function(arr, fn) {
    return arr.sort((a, b) => fn(a) - fn(b));
};
```
