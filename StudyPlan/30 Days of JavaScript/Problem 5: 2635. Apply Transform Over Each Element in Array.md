# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to apply a given mapping function to each element in the input array and return a new array with the transformed values.

# Approach
<!-- Describe your approach to solving the problem. -->
1. These are comment delimiters for a multi-line comment to help explain and document code while preventing ignored text from executing. These comments are commonly used in formal documentation for better code understanding.

    ```
    /**
    * Multi-line comment
    */
    ```

2. This is a special type of comment called a JSDoc comment that explains that the function should take parameters named `arr` and `fn`, which are expected to be an array of numbers and a function.

    ```
    @param {number[]} arr
    @param {Function} fn
    ```

3. This is a special type of comment called a JSDoc comment that explains what the code should return, which, in this case, is an array of numbers. It helps developers and tools like code editors and documentation generators know what the function is supposed to produce.

    ```
    @return {number[]}
    ```

4. This is how we define a function named `map` that takes an array `arr` and a function `fn` as input parameters.

    ```
    var map = function(arr, fn) {
        // code to be executed
    };
    ```

5. This is how we can apply the built-in `map` method of arrays to iterate over each `element` and `index` in the input array `arr`.

    ```
    return arr.map((element, index) => {
        // code to be executed
    };
    ```

6. This calls the provided mapping function `fn` with the `element` and `index` as arguments for each `element` and `index` pair.

    ```
    return fn(element, index);
    ```

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the length of the input array. This is because the function iterates over each element in the array and applies the provided function to it.

- Space complexity: $O(n)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
`n` is the length of the input array. This is because we create a new array to store and return the transformed values.

# Code
```
/**
 * @param {number[]} arr
 * @param {Function} fn
 * @return {number[]}
 */
var map = function(arr, fn) {
    return arr.map((element, index) => {
        return fn(element, index);
  });
};
```
