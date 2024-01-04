# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to design a `Calculator` class that supports basic arithmetic operations and method chaining.

# Approach
<!-- Describe your approach to solving the problem. -->
1. This initializes a new instance of the `Calculator` class with the provided `value` as the starting `result`

    ```
    /** 
     * @param {number} value
     */
    constructor(value) {
        this.result = value
    }
    ```

2. `add` → this method adds the given number `value` to the `result` and returns the updated `Calculator`

    ```
    /** 
     * @param {number} value
     * @return {Calculator}
     */
    add(value){
        this.result += value;
        return this
    }
    ```

3. `subtract` → this method subtracts the given number `value` from the `result` and returns the updated `Calculator`

    ```
    /** 
     * @param {number} value
     * @return {Calculator}
     */
    subtract(value){
        this.result -= value
        return this
    }
    ```

4. `multiply` → this method multiplies the `result`  by the given number `value` and returns the updated `Calculator`

    ```
    /** 
     * @param {number} value
     * @return {Calculator}
     */  
    multiply(value) {
        this.result *= value
        return this
    }
    ```

5. `divide` → this method divides the `result` by the given number `value` and returns the updated `Calculator`

    ```
    /** 
     * @param {number} value
     * @return {Calculator}
     */
    divide(value) {
        if(value === 0 ) throw new Error("Division by zero is not allowed") 
        this.result  = this.result / value
        return this
    }
    ```

6. `power` → this method raises the `result` to the power of the given number `value` and returns the updated `Calculator`

    ```
    /** 
     * @param {number} value
     * @return {Calculator}
     */
    power(value) {
        this.result = Math.pow(this.result,value)
        return this
    }
    ```

7. `getResult` → this method returns the `result`

    ```
    /** 
     * @return {number}
     */
    getResult() {
        return this.result
    }
    ```


# Complexity
- Time complexity: $O(1)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
This is because the methods perform a single mathematical operation and update the variable, which takes a constant amount of time regardless of the size of the input.

- Space complexity: $O(1)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
This is because the class only uses a single variable to store the current value.

# Code
```
class Calculator {

    /** 
     * @param {number} value
     */
    constructor(value) {
        this.result = value
    }

    /** 
     * @param {number} value
     * @return {Calculator}
     */
    add(value){
        this.result += value;
        return this
    }

    /** 
     * @param {number} value
     * @return {Calculator}
     */
    subtract(value){
        this.result -= value
        return this
    }

    /** 
     * @param {number} value
     * @return {Calculator}
     */  
    multiply(value) {
        this.result *= value
        return this
    }

    /** 
     * @param {number} value
     * @return {Calculator}
     */
    divide(value) {
        if(value === 0 ) throw new Error("Division by zero is not allowed") 
        this.result  = this.result / value
        return this
  }

    /** 
     * @param {number} value
     * @return {Calculator}
     */
    power(value) {
        this.result = Math.pow(this.result,value)
        return this
    }

    /** 
     * @return {number}
     */
    getResult() {
        return this.result
    }
}
```
