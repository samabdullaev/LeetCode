# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to count and return the number of arguments passed to a function.

# Approach
<!-- Describe your approach to solving the problem. -->
1. These are comment delimiters for a multi-line comment to help explain and document code while preventing ignored text from executing. These comments are commonly used in formal documentation for better code understanding.

    ```
    /**
    * Multi-line comment
    */
    ```

2. This is a special type of comment called a JSDoc comment that explains that the function should take a parameter named `args`, which can be to be of various types: `null`, `boolean`, `number`, `string`, `Array`, or `Object`.

    ```
    @param {...(null|boolean|number|string|Array|Object)} args
    ```

3. This is a special type of comment called a JSDoc comment that explains what the code should return, which, in this case, is a `number`. It helps developers and tools like code editors and documentation generators know what the function is supposed to produce.

    ```
    @return {number}
    ```

4. This is how we define a function named `argumentsLength` that takes any number of arguments and collects them into an array named `args`.

    ```
    var argumentsLength = function(...args) {
        // code to be executed
    };
    ```

5. This returns the length of the `args` array, which is the count of arguments passed to the function.

    ```
    return args.length;
    ```

# Complexity
- Time complexity: $O(1)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
This because the length of the arguments array is directly returned, and accessing the length of an array has a constant time complexity.

- Space complexity: $O(1)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
This is because the function only uses a constant amount of additional space to store the arguments array.

# Code
```
/**
 * @param {...(null|boolean|number|string|Array|Object)} args
 * @return {number}
 */
var argumentsLength = function(...args) {
    return args.length;
};
```
