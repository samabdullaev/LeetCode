# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to implement a memoized version of the given function. 

> `Memoized function` → a function that will never be called twice with the same inputs. Instead it will return a cached value.

Pre-defined input functions:

1. `sum` → This function accepts two integers `a` and `b` and returns `a + b`.

2. `fib` → This function accepts a single integer `n` and returns 1 if `n <= 1` or `fib(n - 1) + fib(n - 2)` otherwise.

3. `factorial` → This function accepts a single integer `n` and returns 1 if `n <= 1` or `factorial(n - 1) * n` otherwise.

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

4. This is how we define a function named `memoize` that takes a function `fn` as an input parameter.

    ```
    function memoize(fn) {
        // code to be executed
    };
    ```

5. This is how we can initialize a new Map called `map` to store cached results.

    ```
    const map = new Map();
    ```

6. This initializes a variable `callCount` to keep track of how many times the original function was called.

    ```
    var callCount=0
    ```

7. This is how we return a new function that takes any number of arguments represented as `...args`.

    ```
    return function(...args) {
        // code to be executed
    }
    ```

8. This calculates a unique key based on the input arguments (if there's only one argument - it uses it as the key; if there are two arguments - this concatenates them with a large number to ensure uniqueness; if there are no arguments - it sets the key to 0).

    ```
    const key = args[0] + (args[1] ? args[1]*10001 : 0)
    ```

9. If there are no arguments, we should increment `callCount` to count the function calls without arguments.

    ```
    if(args.length==0) callCount++
    ```

10. We then check if the key exists in the map (if the key is not in the map, we will call the original function `fn` with the provided arguments and store the result in the map with the calculated key).

    ```
    if (!map.has(key)){
        map.set(key,fn(...args))
    }
    ```

11. Finally, we will return the cached result corresponding to the key.

    ```
    return map.get(key)
    ```

# Complexity
- Time complexity: $O(1)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
This is because the map data structure provides constant time complexity for the lookup and insertion operations in the map.

- Space complexity: $O(n)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
`n` is the number of unique calls. This is because all unique function calls might be made in the worst case.

# Code
```
/**
 * @param {Function} fn
 * @return {Function}
 */
function memoize(fn) {
    const map = new Map();
    var callCount=0
    return function(...args) {
        const key = args[0] + (args[1] ? args[1]*10001 : 0)
        if(args.length==0) callCount++
        if (!map.has(key)){
            map.set(key,fn(...args))
        }
        return map.get(key)
    }
}
```
