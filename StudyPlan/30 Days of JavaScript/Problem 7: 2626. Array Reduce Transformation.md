# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to reduce an integer array using a custom reduction function and an initial value. This includes iteratively applying the reduction function to each element in the array and the current accumulated value. If the array is empty, we should return the initial value.

# Approach
<!-- Describe your approach to solving the problem. -->
1. These are comment delimiters for a multi-line comment to help explain and document code while preventing ignored text from executing. These comments are commonly used in formal documentation for better code understanding.

    ```
    /**
    * Multi-line comment
    */
    ```

2. This is a special type of comment called a JSDoc comment that explains that the function should take parameters named `nums`, `fn` and `init`, which are expected to be an array of numbers, a function and a number.

    ```
    @param {number[]} nums
    @param {Function} fn
    @param {number} init
    ```

3. This is a special type of comment called a JSDoc comment that explains what the code should return, which, in this case, is a number. It helps developers and tools like code editors and documentation generators know what the function is supposed to produce.

    ```
    @return {number}
    ```

4. This is how we define a function named reduce that takes an array `nums`, a function `fn` and a number `init` as input parameters.

    ```
    var reduce = function(nums, fn, init) {
        // code to be executed
    };
    ```

5. This is how we can initialize a variable `sum` with the value of `init` that will be used to store the final result.

    ```
    let sum = init
    ```

6. This starts a for loop that iterates through the elements of the input array `nums` using the variable `i` as the index.

    ```
    for(let i = 0; i < nums.length; i++) {
        // code to be executed
    }
    ```

7. Inside the loop, we apply the custom function `fn` to the current value of `sum` and the current element in the `nums` array, updating the value of `sum`.

    ```
    sum = fn(sum, nums[i])
    ```

8. After the loop, we should return the final value of `sum`, which is the result of reducing the array.

    ```
    return sum
    ```

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the length of the input array. This is because the function iterates through each element in the array once.

- Space complexity: $O(1)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
This is because it only uses a constant amount of additional space to store the `sum` and the loop counter.

# Code
```
/**
 * @param {number[]} nums
 * @param {Function} fn
 * @param {number} init
 * @return {number}
 */
var reduce = function(nums, fn, init) {
    let sum = init
    for(let i = 0; i < nums.length; i++) {
        sum = fn(sum, nums[i])
    }
    return sum
};
```
