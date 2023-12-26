# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to implement the function that adds a `last()` method to all arrays, which allows to retrieve the last element, and return -1 if the array is empty.

# Approach
<!-- Describe your approach to solving the problem. -->
1. These are comment delimiters for a multi-line comment to help explain and document code while preventing ignored text from executing. These comments are commonly used in formal documentation for better code understanding.

    ```
    /**
    * Multi-line comment
    */
    ```

2. This is a special type of comment called a JSDoc comment that explains what the code should return, which, in this case, is an a value that can be of type: null, boolean, number, string, array, or object. It helps developers and tools like code editors and documentation generators know what the function is supposed to produce.

    ```
    @return {null|boolean|number|string|Array|Object}
    ```

3. This is how we define a function that adds a new method named `last` to the prototype of all arrays.

    ```
    Array.prototype.last = function() {
        // code to be executed
    };
    ```

4. This checks if the array is empty and returns 1 if it is `true`.

    ```
    if (this.length == 0) {return -1;} 
    ```

5. This returns the last element of the array if the array is not empty.

    ```
    else {return this[this.length - 1];}
    ```

# Complexity
- Time complexity: $O(1)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
This is because accessing the last element of an array takes constant time.

- Space complexity: $O(1)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
This is because the code does not use any additional space that grows with the size of the input array.

# Code
```
/**
 * @return {null|boolean|number|string|Array|Object}
 */
Array.prototype.last = function() {
    if (this.length == 0) {return -1;} 
    else {return this[this.length - 1];}
};
```
