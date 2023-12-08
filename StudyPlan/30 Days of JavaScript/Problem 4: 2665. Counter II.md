# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
Pre-defined functions:

1. `increment()` method → This increases the current value by 1 and then returns it

2. `decrement()` method → This reduces the current value by 1 and then returns it

3. `reset()` method → This sets the current value to `init` and then returns it

We need to create a a counter object that should accept an initial integer and return that with three functions.

# Approach
<!-- Describe your approach to solving the problem. -->
1. These are comment delimiters for a multi-line comment to help explain and document code while preventing ignored text from executing. These comments are commonly used in formal documentation for better code understanding.

    ```
    /**
    * Multi-line comment
    */
    ```

2. This is a special type of comment called a JSDoc comment that explains that the function should take a parameter named `init`, which is expected to be an `integer`.

    ```
    @param {integer} init
    ```

3. This is a special type of comment called a JSDoc comment that explains what the code should return, which, in this case, is an `Object` with 3 functions. It helps developers and tools like code editors and documentation generators know what the function is supposed to produce.

    ```
    @return { increment: Function, decrement: Function, reset: Function }
    ```
4. This is how we define a function named `createCounter` that takes an integer `init` as input.

    ```
    var createCounter = function(init) {
        // code to be executed
    };
    ```

5. This is how we can initialize a variable `count` with the value of `init` that will be used to keep track of the current count.

    ```
    let count = init;
    ```

6. This is how we can return an `Object` with 3 methods.

    ```
    return {
        // Method 1: code to be executed

        // Method 2: code to be executed

        // Method 3: code to be executed
    };
    ```

7. This defines the first method called `increment` that increments the `count` by 1 and returns the updated value.

    ```
    increment: function() {
        count++;
        return count;
    }
    ```

8. This defines the second method called `decrement` that decrements the `count` by 1 and returns the updated value.

    ```
    decrement: function() {
        count--;
        return count;
    }
    ```

9. This defines the third method called `reset` that sets the `count` back to the initial integer value `init` and returns it.

    ```
    reset: function() {
        count = init;
        return count;
    }
    ```

# Complexity
- Time complexity: $O(1)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
This is because the code performs simple arithmetic operations.

- Space complexity: $O(1)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
This is because it only uses a constant amount of additional space to store the variable.

# Code
```
/**
 * @param {integer} init
 * @return { increment: Function, decrement: Function, reset: Function }
 */
var createCounter = function(init) {
    let count = init;
    return {
        increment: function() {
            count++;
            return count;
        },
        decrement: function() {
            count--;
            return count;
        },
        reset: function() {
            count = init;
            return count;
        }
    }
};
```
