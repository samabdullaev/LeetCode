# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to create a new promise that resolves with the sum of two numbers obtained from `promise1` and `promise2`, ensuring both promises have resolved first.

# Approach
<!-- Describe your approach to solving the problem. -->
1. These are comment delimiters for a multi-line comment to help explain and document code while preventing ignored text from executing. These comments are commonly used in formal documentation for better code understanding.

    ```
    /**
    * Multi-line comment
    */
    ```

2. This is a special type of comment called a JSDoc comment that explains that the function should take parameters named `promise1` and `promise2`, which are expected to be `Promise`.

    ```
    @param {Promise} promise1
    @param {Promise} promise2
    ```

3. This is a special type of comment called a JSDoc comment that explains what the code should return, which, in this case, is a `Promise`. It helps developers and tools like code editors and documentation generators know what the function is supposed to produce.

    ```
    @return {Promise}
    ```

4. This is how we define a function named `addTwoPromises` that takes two promise parameters.

    ```
    var addTwoPromises = async function(promise1, promise2) {
        // code to be executed
    };
    ```

5. This uses `Promise.all` to wait for both `promise1` and `promise2` to resolve. Once both promises have resolved, their values are destructured into `value1` and `value2`.

    ```
    const [value1, value2] = await Promise.all([promise1, promise2]);
    ```

6. This is how we can return a new promise that resolves with the sum of the two numbers.

    ```
    return value1 + value2;
    ```

# Complexity
- Time complexity: $O(1)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
This is because the function only performs a single operation of awaiting the resolution of two promises and then adding their values.

- Space complexity: $O(1) $
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
This is because the function only creates two variables to store the values of the promises, which do not depend on the size of the input.

# Code
```
/**
 * @param {Promise} promise1
 * @param {Promise} promise2
 * @return {Promise}
 */
var addTwoPromises = async function(promise1, promise2) {
    const [value1, value2] = await Promise.all([promise1, promise2]);
    return value1 + value2;
};
```
