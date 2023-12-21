# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to implement a debounced function that delays the execution of a given function by a specified time. If the function is called again within the specified time, the previous execution is canceled. 

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
    @param {number} t milliseconds
    ```

3. This is a special type of comment called a JSDoc comment that explains what the code should return, which, in this case, is a `Function`. It helps developers and tools like code editors and documentation generators know what the function is supposed to produce.

    ```
    @return {Function}
    ```

4. This is how we define a function named `debounce` that takes two argument.

    ```
    var debounce = function(fn, t) {
        // code to be executed
    };
    ```

5. This is how we can initialize a variable `timer` to keep track of the timeout.

    ```
    let timer;
    ```

6. This defines and returns a new function that takes any number of arguments using the rest parameter `...args`.

    ```
    return function(...args) {
        // code to be executed
    }
    ```

7. This clears any previous timeout set using the `timer` variable. If this function is called again before the previous execution, it cancels the previous timeout.

    ```
    clearTimeout(timer);
    ```

8. This schedules the delayed execution of a given function with its arguments and ensures that it only runs after the specified time, canceling previous executions if called within that timeframe.

    ```
    timer = setTimeout(() => fn(...args), t);
    ```

# Complexity
- Time complexity: $O(1)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
This is because the code only performs a constant number of operations regardless of the size of the input.

- Space complexity: $O(1)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
This is because the function only uses a constant amount of memory to store the `timer` variable.

# Code
```
/**
 * @param {Function} fn
 * @param {number} t milliseconds
 * @return {Function}
 */
var debounce = function(fn, t) {
    let timer;
    return function(...args) {
        clearTimeout(timer);
        timer = setTimeout(() => fn(...args), t);
    }
};
```
