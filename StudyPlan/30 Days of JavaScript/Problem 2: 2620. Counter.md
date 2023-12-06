# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to create a counter function that returns the current value and increments it with each call.

# Approach
<!-- Describe your approach to solving the problem. -->
1. These are comment delimiters for a multi-line comment to help explain and document code while preventing ignored text from executing. These comments are commonly used in formal documentation for better code understanding.

    ```
    /**
    * Multi-line comment
    */
    ```

2. This is a special type of comment called a JSDoc comment that explains that the function should take a parameter named `n`, which is expected to be a `number`.

    ```
    @param {number} n
    ```

3. This is a special type of comment called a JSDoc comment that explains what the code should return, which, in this case, is a `Function` called `counter`. It helps developers and tools like code editors and documentation generators know what the function is supposed to produce.

    ```
    @return {Function} counter
    ```

4. This is how we define a function named `createCounter` that takes a number `n` as input.

    ```
    var createCounter = function(n) {
        // code to be executed
    };
    ```

5. This is how we can return another function, which doesn't take any input.

    ```
    return function() {
        // code to be executed
    };
    ```

6. This is the main code that returns the current value of `n` and then increases it by 1.

    ```
    return n++;
    ```

# Complexity
- Time complexity: $O(1)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
This is because the function only performs simple variable retrieval and increment.

- Space complexity: $O(1)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
This is because the function does not use any additional space that grows with the input size.

# Code
```
/**
 * @param {number} n
 * @return {Function} counter
 */
var createCounter = function(n) {
    return function() {
        return n++;
    };
};
```
