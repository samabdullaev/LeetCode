# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to create a function that takes any number of arguments, but when called, always returns the text `"Hello World"`.

# Approach
<!-- Describe your approach to solving the problem. -->
1. These are comment delimiters for a multi-line comment to help explain and document code while preventing ignored text from executing. These comments are commonly used in formal documentation for better code understanding.

    ```
    /**
    * Multi-line comment
    */
    ```

2. This is a special type of comment called a JSDoc comment that explains what the code should return, which, in this case, is a `Function`. It helps developers and tools like code editors and documentation generators know what the function is supposed to produce.

    ```
    @return {Function}
    ```

3. We create a function called `createHelloWorld`, which doesn't need any input.

    ```
    var createHelloWorld = function() {
        // code to be executed
    };
    ```

4. We create a new function that can take multiple inputs, but we don't use these inputs in our task.

    ```
    return function(...args) {
        // code to be executed
    }
    ```

5. We simply return the text `"Hello World"`. This is what the function will always produce as its output.

    ```
    return "Hello World";
    ```

# Complexity
- Time complexity: $O(1)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
This is because it always returns the same string regardless of the input arguments. The number of arguments passed to the returned function does not affect the execution time.

- Space complexity: $O(1)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
This is because we are not storing any data structures that grow with the size of the input.

# Code
```
/**
 * @return {Function}
 */
var createHelloWorld = function() {
    return function(...args) {
        return "Hello World"
    }
};
```
