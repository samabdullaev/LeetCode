# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
Pre-defined methods:
1. `toBe` method → This checks if two values are equal (returns `Not Equal` otherwise)

2. `notToBe` method → This checks if two values are not equal (returns `Equal` otherwise)

We need to create a function that takes in a value and compares it with another given value. 

# Approach
<!-- Describe your approach to solving the problem. -->
1. These are comment delimiters for a multi-line comment to help explain and document code while preventing ignored text from executing. These comments are commonly used in formal documentation for better code understanding.

    ```
    /**
    * Multi-line comment
    */
    ```

2. This is a special type of comment called a JSDoc comment that explains that the function should take a parameter named `val`, which is expected to be a `string`.

    ```
    @param {string} val
    ```

3. This is a special type of comment called a JSDoc comment that explains what the code should return, which, in this case, is an `Object`. It helps developers and tools like code editors and documentation generators know what the function is supposed to produce.

    ```
    @return {Object}
    ```

4. This is how we define a function named `expect` that takes a string `val` as input.

    ```
    var expect = function(val) {
        // code to be executed
    };
    ```

5. This is how we can return an `Object` with 2 methods.

    ```
    return {
        // Method 1: code to be executed

        // Method 2: code to be executed
    };
    ```

6. This defines the first method called `toBe` that takes one argument and checks if it is equal to another given value. This method returns `true` if both values are equal.

    ```
    toBe: (val2) => {
        if (val !== val2) throw new Error("Not Equal");
        else return true;
    }
    ```

7. This defines the second method called `notToBe` that takes one argument and checks if it is not equal to another given value. This method returns `true` if both values are not equal.

    ```
    notToBe: (val2) => {
        if (val === val2) throw new Error("Equal");
        else return true;
    }
    ```

# Complexity
- Time complexity: $O(1)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
This is because both `toBe` and `notToBe` methods perform a simple equality check, which takes constant time.

- Space complexity: $O(1)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
This is because the code only returns a boolean value and does not store any other variables or data.

# Code
```
/**
 * @param {string} val
 * @return {Object}
 */
var expect = function(val) {
    return {
        toBe: (val2) => {
            if (val !== val2) throw new Error("Not Equal");
            else return true;
        },
        notToBe: (val2) => {
            if (val === val2) throw new Error("Equal");
            else return true;
        }
    }
};
```
