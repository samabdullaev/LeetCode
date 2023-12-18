# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to execute a given function with specified arguments at regular intervals and have the ability to cancel this execution at a certain time.

# Approach
<!-- Describe your approach to solving the problem. -->
1. These are comment delimiters for a multi-line comment to help explain and document code while preventing ignored text from executing. These comments are commonly used in formal documentation for better code understanding.

    ```
    /**
    * Multi-line comment
    */
    ```

2. This is a special type of comment called a JSDoc comment that explains that the function should take parameters named `fn`, `args` and `t`, which are expected to be `Function`, `Array` and a `number`.

    ```
    @param {Function} fn
    @param {Array} args
    @param {number} t
    ```

3. This is a special type of comment called a JSDoc comment that explains what the code should return, which, in this case, is a `Function`. It helps developers and tools like code editors and documentation generators know what the function is supposed to produce.

    ```
    @return {Function}
    ```

4. This is how we define a function named `cancellable` that takes three parameters.

    ```
    var cancellable = function(fn, args, t) {
        // code to be executed
    };
    ```

5. This calls the given function `fn` with the provided arguments `...args`, resulting in the immediate execution of the function.

    ```
    fn(...args);
    ```

6. This is how we can establishe a recurring execution of the function `fn` with the given arguments `...args` at intervals of `t` milliseconds and keep track of this interval using the `timer` variable.

    ```
    let timer = setInterval(() => fn(...args), t);
    ```

7. This creates a function named `cancelFn`, which cancels the scheduled interval execution of the function when it is invoked by the caller.

    ```
    let cancelFn = () => clearInterval(timer);
    ```

8. This returns the `cancelFn` function, which can be used to stop the interval execution of the provided function.

    ```
    return cancelFn;
    ```

# Complexity
- Time complexity: $O(1)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
This is because the function always performs a constant number of operations, regardless of the size of the input.

- Space complexity: $O(1)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
This is because the code only uses a constant amount of memory to store the variables `timer`, `cancelFn`, and the arguments passed to `fn`.

# Code
```
/**
 * @param {Function} fn
 * @param {Array} args
 * @param {number} t
 * @return {Function}
 */
var cancellable = function(fn, args, t) {
    fn(...args);
    let timer = setInterval(() => fn(...args), t);

    let cancelFn = () => clearInterval(timer);
    return cancelFn;
};
```
