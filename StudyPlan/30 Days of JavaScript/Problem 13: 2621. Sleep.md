# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to implement an asynchronous function that can resolve any value after sleeping for a given number of milliseconds.

# Approach
<!-- Describe your approach to solving the problem. -->
1. These are comment delimiters for a multi-line comment to help explain and document code while preventing ignored text from executing. These comments are commonly used in formal documentation for better code understanding.

    ```
    /**
    * Multi-line comment
    */
    ```

2. This is a special type of comment called a JSDoc comment that explains that the function should take a parameter named `millis`, which is expected to be a `number`.

    ```
    @param {number} millis
    ```

3. This is a special type of comment called a JSDoc comment that explains what the code should return, which, in this case, is a `Promise`. It helps developers and tools like code editors and documentation generators know what the function is supposed to produce.

    ```
    @return {Promise}
    ```

4. This is how we define an asynchronous function named `sleep` that takes a single argument, `millis`.

    ```
    async function sleep(millis) {
        // code to be executed
    };
    ``` 

5. This is how we can create a new `Promise` and use `await` to pause the execution of this function until the `Promise` resolves.

    ```
    await new Promise((resolve) => {
        // code to be executed
    })
    ```

6. This uses the `setTimeout` function to delay the execution of the `resolve` function for the specified number of `millis` milliseconds, creating a time delay.

    ```
    setTimeout(resolve, millis)
    ```

# Complexity
- Time complexity: $O(1)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
This is because the code always introduces a consistent time delay, regardless of the input.

- Space complexity: $O(1)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
This is because the code only uses a fixed amount of memory, regardless of the input size, by creating a single `Promise` object.

# Code
```
/**
 * @param {number} millis
 * @return {Promise}
 */
async function sleep(millis) {
    await new Promise((resolve) => {
        setTimeout(resolve, millis)
    })
}
```
