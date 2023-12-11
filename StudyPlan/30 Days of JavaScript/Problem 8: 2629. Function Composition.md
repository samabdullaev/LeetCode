# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to return a new function that is the function composition of the array of functions. 

# Approach
<!-- Describe your approach to solving the problem. -->
1. These are comment delimiters for a multi-line comment to help explain and document code while preventing ignored text from executing. These comments are commonly used in formal documentation for better code understanding.

    ```
    /**
    * Multi-line comment
    */
    ```

2. This is a special type of comment called a JSDoc comment that explains that the function should take an array of `functions` as input.

    ```
    @param {Function[]} functions
    ```

3. This is a special type of comment called a JSDoc comment that explains what the code should return, which, in this case, is a `function`. It helps developers and tools like code editors and documentation generators know what the function is supposed to produce.

    ```
    @return {Function}
    ```

4. This is how we define a function named `compose` that takes an array of `functions` as input.

    ```
    var compose = function(functions) {
        // code to be executed
    };
    ```

5. This is an inner function that takes a single integer `x` as input.

    ```
    return function(x) {
        // code to be executed
    };
    ```

6. This is how we can initialize a variable `result` with the input value `x` that will be used to hold the result of the function composition.

    ```
    let result = x;
    ```

7. This starts a for loop that iterates through the array of `functions` in reverse order, starting from the last function.

    ```
    for (let i = functions.length - 1; i >= 0; i--) {
        // code to be executed
    }
    ```

8. In each iteration of the loop, we apply the `i`-th function to the current value of `result`, which effectively composes the functions from right to left.

    ```
    result = functions[i](result);
    ```

9. This returns the `result` after applying all the functions in the array.

    ```
    return result;
    ```

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of functions in the input array. This is because the function iterates over the array of functions once, applying each function to the result.

- Space complexity: $O(1)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
This is because it only uses a constant amount of additional space to store the result and the loop variable.

# Code
```
/**
 * @param {Function[]} functions
 * @return {Function}
 */
var compose = function(functions) {
    return function(x) {
        let result = x;
        for (let i = functions.length - 1; i >= 0; i--) {
            result = functions[i](result);
        }
        return result;
    };
};
```
