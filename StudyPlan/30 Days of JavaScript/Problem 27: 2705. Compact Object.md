# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to remove keys with falsy values from the given object or array. 

> `Compact object` → the same as the original object, except with keys containing falsy values removed. This operation applies to the object and any nested objects. Arrays are considered objects where the indices are keys. A value is considered falsy when Boolean(value) returns `false`.

# Approach
<!-- Describe your approach to solving the problem. -->
1. These are comment delimiters for a multi-line comment to help explain and document code while preventing ignored text from executing. These comments are commonly used in formal documentation for better code understanding.

    ```
    /**
    * Multi-line comment
    */
    ```

2. This is a special type of comment called a JSDoc comment that explains that the function should take a parameter named `obj`, which is expected to be an `Object` or an `Array`.

    ```
    @param {Object|Array} obj
    ```

3. This is a special type of comment called a JSDoc comment that explains what the code should return, which, in this case, is either an `Object` or an `Array`. It helps developers and tools like code editors and documentation generators know what the function is supposed to produce.

    ```
    @return {Object|Array}
    ```

4. This is how we define a function named `compactObject` that takes an object or an array as its argument.

    ```
    var compactObject = function(obj) {
        // code to be executed
    };
    ```

5. This checks if the input object is `null`.

    ```
    if (obj === null) return null;
    ```

6. This filters out falsy values and apply the `compactObject` function recursively to each element in the array if the input is an array.

    ```
    if (Array.isArray(obj)) return obj.filter(Boolean).map(compactObject);
    ```

7. This returns the input as it is if the input is neither `null` nor an array nor an object.

    ```
    if (typeof obj !== "object") return obj;
    ```

8. This is how we can create an empty object named `compacted` to store the result.

    ```
    const compacted = {};
    ```

9. This iterates through each key-value pair in the input object, applies the `compactObject` function to the value, and adds the key-value pair to the compacted object if the resulting value is truthy.

    ```
    for (const key in obj) {
        let value = compactObject(obj[key]);
            if (Boolean(value)) compacted[key] = value;
    }
    ```

10. This function returns either an object or an array.

    ```
    return compacted;
    ```

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the total number of elements in the input object. This is because the function iterates through each key-value pair in the object and recursively calls itself for nested objects or arrays.

- Space complexity: $O(n)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
`n` is the total number of elements in the input object. This is because the function creates a new object to store the compacted key-value pairs. 

# Code
```
/**
 * @param {Object|Array} obj
 * @return {Object|Array}
 */
var compactObject = function(obj) {
    if (obj === null) return null;
    if (Array.isArray(obj)) return obj.filter(Boolean).map(compactObject);
    if (typeof obj !== "object") return obj;
    
    const compacted = {};
    
    for (const key in obj) {
        let value = compactObject(obj[key]);
        if (Boolean(value)) compacted[key] = value;
    }

    return compacted;
};
```
