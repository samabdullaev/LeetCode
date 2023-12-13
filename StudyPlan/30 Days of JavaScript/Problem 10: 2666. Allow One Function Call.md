# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to create and return a new function that behaves like the original function, but ensures that it is called at most once.

> The first time the returned function is called → it should return the same result as the original function

> Every subsequent time it is called → it should return `undefined`

# Approach
<!-- Describe your approach to solving the problem. -->
1. These are comment delimiters for a multi-line comment to help explain and document code while preventing ignored text from executing. These comments are commonly used in formal documentation for better code understanding.

    ```
    /**
    * Multi-line comment
    */
    ```

2. This is a special type of comment called a JSDoc comment that explains that the function should take a parameter named `fn`, which is expected to be a `Function`.

    ```
    @param {Function} fn
    ```

3. This is a special type of comment called a JSDoc comment that explains what the code should return, which, in this case, is a `Function`. It helps developers and tools like code editors and documentation generators know what the function is supposed to produce.

    ```
    @return {Function}
    ```

4. This is how we define a function named `once` that takes a function `fn` as an input parameter.

    ```
    var once = function(fn) {
        // code to be executed
    };
    ```

5. This is how we can initialize a variable `call` to 0 where we will keep track of whether the function has been called.

    ```
    let call = 0
    ```

6. This is how we return a new function that takes any number of arguments represented as `...args`.

    ```
    return function(...args) {
        // code to be executed
    }
    ```

7. This checks if the `call` variable is equal to 0 (i.e., the function has not been called yet).

    ```
    if(!call) {
        // code to be executed
    }
    ```

8. If the condition in is true (i.e., the function hasn't been called), this line sets call to 1, indicating that the function is being called.

    ```
    call = 1
    ```

9. This calls the original function `fn` with the provided arguments `...args` and returns the result of this function call.

    ```
    return fn(...args)
    ```

# Complexity
- Time complexity: $O(1)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
This is because the function involves a single check and a potential function call which only executes once regardless of the size of the input.

- Space complexity: $O(1)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
This is because the code only requires a single flag variable.

# Code
```
/**
 * @param {Function} fn
 * @return {Function}
 */
var once = function(fn) {
    let call = 0
    return function(...args) {
        if(!call) {
            call = 1
            return fn(...args)
        }
    }
};
```
