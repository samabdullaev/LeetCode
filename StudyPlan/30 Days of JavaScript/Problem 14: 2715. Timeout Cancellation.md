# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to implement a function that schedules the execution of a given function with arguments after a specified timeout. We should also provide a way to cancel the execution if required before the timeout. 

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
    const cancellable = function(fn, args, t) {
        // code to be executed
    };
    ```

5. This is how we define a function named `cancelFn` that cancels the scheduled execution of `fn` by clearing the timer responsible for its execution.

    ```
    const cancelFn = function (){
        clearTimeout(timer);
    };
    ```

6. This is how we define a function named `timer` and use `setTimeout` to schedule the execution of the `fn` function with the provided arguments `...args` after a specified timeout `t` in milliseconds.

    ```
    const timer = setTimeout(()=>{
        fn(...args)
    }, t);
    ```

7. This returns the `cancelFn` function, which is used to cancel the scheduled execution of `fn`.

    ```
    return cancelFn;
    ```

# Complexity
- Time complexity: $O(1)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
This is because the function only performs a constant number of operations, regardless of the size of the input.

- Space complexity: $O(1)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
This is because the code only uses a constant amount of memory to store the variables `cancelFn` and `timer`.

# Code
```
/**
 * @param {Function} fn
 * @param {Array} args
 * @param {number} t
 * @return {Function}
 */
const cancellable = function(fn, args, t) {
    const cancelFn = function (){
        clearTimeout(timer);
    };
    const timer = setTimeout(()=>{
        fn(...args)
    }, t);
    return cancelFn;
};
```
