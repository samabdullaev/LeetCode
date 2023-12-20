# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to create a class that stores and retrieves key-value pairs, but with an additional feature where each key has an associated expiration time, and after that time has passed, the key should no longer be accessible.

Pre-defined public methods:

1. `set(key, value, duration)` → This method sets a key-value pair with an expiration time in milliseconds; returns `true` if the key already existed and had not expired, `false` otherwise, and updates the value and duration if the key already exists.

2. `get(key)` → This method retrieves the value associated with a key if it's still valid and has not expired, otherwise returns -1.

3. `count()` → This method returns the number of non-expired keys in the cache, indicating how many key-value pairs are still accessible.

# Approach
<!-- Describe your approach to solving the problem. -->
1. These are comment delimiters for a multi-line comment to help explain and document code while preventing ignored text from executing. These comments are commonly used in formal documentation for better code understanding.

    ```
    /**
     * Multi-line comment
     */
    ```

2. This constructor initializes a new cache by creating an empty JavaScript `Map` that will be used to store key-value pairs with associated expiration times.

    ```
    function TimeLimitedCache() {
        this.cache = new Map();
    }
    ```

3. `Set method` → This method sets a key-value pair with a specified expiration time. It checks if the key already exists, clears any existing timeout for that key, sets a new timeout for expiration, and updates or adds the key-value pair to the cache. It returns `true` if the key already existed, otherwise `false`.

    ```
    TimeLimitedCache.prototype.set = function(key, value, duration) {
        const valueInCache = this.cache.get(key);
        if (valueInCache) {
            clearTimeout(valueInCache.timeout);
        }
        const timeout = setTimeout(
            () => this.cache.delete(key), duration
        );
        this.cache.set(key, { value, timeout });
        return Boolean(valueInCache);
    };
    ```

4. `Get method` → This method retrieves the value associated with a key if it exists in the cache and has not expired. If the key is found and still valid, it returns the associated value. If the key is not found or has expired, it returns -1.

    ```
    TimeLimitedCache.prototype.get = function(key) {
        return this.cache.has(key) ? this.cache.get(key).value : -1;
    };
    ```

5. `Count method` → This method returns the count of non-expired keys in the cache, which represents the number of key-value pairs that are still valid and haven't expired.

    ```
    TimeLimitedCache.prototype.count = function() {
        return this.cache.size;
        };
    ```

# Complexity
- Time complexity: $O(1)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
This is because both the set and get methods involve basic Map operations that have constant time complexity on average.

- Space complexity: $O(n)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
`n` is the number of unique key-value pairs stored in the cache. This is because the cache is implemented using a Map data structure, which requires space to store the keys and values.

# Code
```
function TimeLimitedCache() {
  this.cache = new Map();
}

/** 
 * @param {number} key
 * @param {number} value
 * @param {number} time until expiration in ms
 * @return {boolean} if un-expired key already existed
 */
TimeLimitedCache.prototype.set = function(key, value, duration) {
    const valueInCache = this.cache.get(key);
    if (valueInCache) {
        clearTimeout(valueInCache.timeout);
    }
    const timeout = setTimeout(() => this.cache.delete(key), duration);
    this.cache.set(key, { value, timeout });
    return Boolean(valueInCache);
};

/** 
 * @param {number} key
 * @return {number} value associated with key
 */
TimeLimitedCache.prototype.get = function(key) {
    return this.cache.has(key) ? this.cache.get(key).value : -1;
};

/** 
 * @return {number} count of non-expired keys
 */
TimeLimitedCache.prototype.count = function() {
    return this.cache.size;
};
```
