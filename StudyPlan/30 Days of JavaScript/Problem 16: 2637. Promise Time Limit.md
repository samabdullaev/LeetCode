# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to create a time-limited version of an asynchronous function. Our goal is to make sure the function completes within a specified time limit, and if it exceeds this limit, it should be rejected with the speciifed message.


# Approach
<!-- Describe your approach to solving the problem. -->
1. These are comment delimiters for a multi-line comment to help explain and document code while preventing ignored text from executing. These comments are commonly used in formal documentation for better code understanding.

    ```
    /**
    * Multi-line comment
    */
    ```

2. This is a special type of comment called a JSDoc comment that explains that the function should take parameters named `fn` and `t`, which are expected to be `Function` and a `number`.

    ```
    @param {Function} fn
    @param {number} t
    ```

3. This is a special type of comment called a JSDoc comment that explains what the code should return, which, in this case, is a `Function`. It helps developers and tools like code editors and documentation generators know what the function is supposed to produce.

    ```
    @return {Function}
    ```

4. This is how we define a function named `timeLimit` that takes two parameters.

    ```
    var timeLimit = function(fn, t) {
        // code to be executed
    };
    ```

5. This returns an asynchronous function that can take any number of arguments represented as `...args`.

    ```
    return async function(...args) {
        // code to be executed
    };
    ```

6. This is how we can use `Promise.race` to create a race condition between two promises.

    ```
    return Promise.race([
        // code to be executed
    ]);
    ```

7. This calls the original function `fn` with the provided arguments `...args`.

    ```
    fn(...args)
    ```

8. This creates a new promise with a function that immediately schedules a rejection with the specified message after a specified time `t` in milliseconds.

    ```
    new Promise((_, reject) => {
        setTimeout(() => reject('Time Limit Exceeded'), t)
    })
    ```

# Complexity
- Time complexity: $O(1)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
This is because the code only performs a constant number of operations, regardless of the size of the input.

- Space complexity: $O(1)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
This is because the function does not use any additional space that grows with the size of the input.

# Code
```
/**
 * @param {Function} fn
 * @param {number} t
 * @return {Function}
 */
var timeLimit = function(fn, t) {  
    return async function(...args) {
        return Promise.race([
            fn(...args),
            new Promise((_, reject) => {
                setTimeout(() => reject('Time Limit Exceeded'), t)
            })
        ]);
    }
};
```
