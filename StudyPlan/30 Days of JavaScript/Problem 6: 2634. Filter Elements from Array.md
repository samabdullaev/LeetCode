# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to filter elements from an array based on a provided filtering function. This requires iterating through the array and only keeping elements for which the given function returns a truthy value.

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

4. This is how we define a function named `filter` that takes an array `arr` and a function `fn` as input parameters.

    ```
    var filter = function(arr, fn) {
        // code to be executed
    };
    ```

5. This is how we can initialize an empty array called `result` where we will store the filtered elements.

    ```
    var result = [];
    ```

6. This starts a for loop that iterates through the elements of the input array `arr` using the variable `i` as the index.

    ```
    for (var i = 0; i < arr.length; i++) {
        // code to be executed
    }
    ```

7. It checks if the function `fn` (provided as a parameter) returns a truthy value when called with the current element `arr[i]` and its index `i`.

    ```
    if (fn(arr[i], i)) {
        // code to be executed
    }
    ```

8. This adds the current element `arr[i]` to the result array if the condition is true.

    ```
    result.push(arr[i]);
    ```

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the length of the input array. This is because the function iterates through each element of the array once.

- Space complexity: $O(n)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
This is because the function creates a new array `result` to store the filtered elements. It might store all elements in the worst case.

# Code
```
/**
 * @param {number[]} arr
 * @param {Function} fn
 * @return {number[]}
 */
var filter = function(arr, fn) {
    var result = [];
    for (var i = 0; i < arr.length; i++) {
        if (fn(arr[i], i)) {
            result.push(arr[i]);
        }
    }
    return result;
};
```
