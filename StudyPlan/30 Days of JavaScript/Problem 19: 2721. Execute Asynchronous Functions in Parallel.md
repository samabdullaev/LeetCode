# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to execute multiple asynchronous functions concurrently and handle their results collectively. The key is to keep track of the number of completed functions and resolve or reject the main promise accordingly.

1. `promise resolves`

    - when all asynchronous functions in the array have successfully completed in parallel, and the resolved value is an array containing the values of each resolved promise in the order they were in the original array.

2. `promise rejects`

    - when any promise returned by the functions is rejected, the main promise also rejects with the reason of the first encountered rejection.

# Approach
<!-- Describe your approach to solving the problem. -->
1. These are comment delimiters for a multi-line comment to help explain and document code while preventing ignored text from executing. These comments are commonly used in formal documentation for better code understanding.

    ```
    /**
    * Multi-line comment
    */
    ```

2. This is a special type of comment called a JSDoc comment that explains that the function should take a parameter named `functions`, which is expected to be an `Array` of `functions`.

    ```
    @param {Array<Function>} functions
    ```

3. This is a special type of comment called a JSDoc comment that explains what the code should return, which, in this case, is a `Promise` that will resolve to an array of results or reject with an error. It helps developers and tools like code editors and documentation generators know what the function is supposed to produce.

    ```
    @return {Promise<any>}
    ```

4. This is how we define a function named `promiseAll` that takes an array of `functions` as its argument.

    ```
    var promiseAll = function(functions) {
        // code to be executed
    };
    ```

5. This is how we can create a new `Promise` with `resolve` and `reject` functions as parameters.

    ```
    return new Promise((resolve, reject) => {
        // code to be executed
    })
    ```

6. This creates an array named `results` to store the results of the asynchronous functions.

    ```
    let results = new Array(functions.length);
    ```

7. This is how we can initialize a counter named `count` to track the number of completed functions.

    ```
    let count = 0;
    ```

8. This function executes an array of asynchronous functions concurrently, collects their results, and resolves a main promise with the array of results when all functions have completed successfully, or rejects with the first encountered error.

    ```
    functions.forEach((fn, i) => {
        fn()
        .then(val => {
            results[i] = val;
            count++;
            if(count === functions.length) resolve(results);
        })
        .catch(error => reject(error));
    })
    ```

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of functions in the input array. This is because the function iterates over each function in the array and calls it, which takes constant time.

- Space complexity: $O(n)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
`n` is the number of functions in the input array. This is because the function uses space proportional to the number of functions by creating an array and variables for each iteration of the loop.

# Code
```
/**
 * @param {Array<Function>} functions
 * @return {Promise<any>}
 */
var promiseAll = function(functions) {
    return new Promise((resolve, reject) => {
        let results = new Array(functions.length);
        let count = 0;
        functions.forEach((fn, i) => {
            fn()
            .then(val => {
                results[i] = val;
                count++;
                if(count === functions.length) resolve(results);
            })
            .catch(error => reject(error));
        })
    })
};
```
