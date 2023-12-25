# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to return a chunked array from the given array, where each subarray has a specified size, and the last subarray may have a length less than the size if the original array's length is not evenly divisible by the specified size.

# Approach
<!-- Describe your approach to solving the problem. -->
1. These are comment delimiters for a multi-line comment to help explain and document code while preventing ignored text from executing. These comments are commonly used in formal documentation for better code understanding.

    ```
    /**
    * Multi-line comment
    */
    ```

2. This is a special type of comment called a JSDoc comment that explains that the function should take parameters named `arr` and `size`, which are expected to be an `Array` and a `number`.

    ```
    @param {Array} arr
    @param {number} size
    ```

3. This is a special type of comment called a JSDoc comment that explains what the code should return, which, in this case, is an `Array`. It helps developers and tools like code editors and documentation generators know what the function is supposed to produce.

    ```
    @return {Array}
    ```

4. This is how we define a function named `chunk` that takes an array `arr` and a number `size` as its argument.

    ```
    var chunk = function(arr, size) {
        // code to be executed
    };
    ```

5. This is how we can initialize an empty array `res` to store the chunked subarrays.

    ```
    const res = []
    ```

6. This loop iterates through the input array in chunks of the specified size, extracts each chunk using the `slice` method, and appends it to the result array.

    ```
    for(let  i = 0; i < arr.length; i += size) {
        res.push( arr.slice(i , i + size))
    }
    ```

7. This returns the array `res` containing the chunked subarrays as the output of the function.

    ```
    return res
    ```

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the length of the input array. This is because the function iterates through the array once, with each iteration taking a constant amount of time.

- Space complexity: $O(n)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
`n` is the length of the input array. This is because the result array stores the chunked subarrays, and the size of this array will be proportional to the length of the input array.

# Code
```
/**
 * @param {Array} arr
 * @param {number} size
 * @return {Array}
 */
var chunk = function(arr, size) {
    const res = []
    for(let  i = 0; i < arr.length; i += size) {
        res.push( arr.slice(i , i + size))
    }
    return res
};
```
