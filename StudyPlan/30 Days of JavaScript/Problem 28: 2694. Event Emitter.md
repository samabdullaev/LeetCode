# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to implement an `EventEmitter` class that allows subscription to events and emitting them.

# Approach
<!-- Describe your approach to solving the problem. -->
1. This initializes the events property as a new `Map`, which will be used to store event names and their associated callback functions.

    ```
    constructor() {
        this.events = new Map();
    }
    ```

2. This method subscribes a callback function to an event, creating a new array of listeners for the event if it doesn't exist, and adds the callback to that array.

    ```
    /**
     * @param {string} eventName
     * @param {Function} callback
     * @return {Object}
     */
    subscribe(eventName, callback) {
        if(!this.events.has(eventName)) {
            this.events.set(eventName, [])
        }
        const listeners = this.events.get(eventName);
        listeners.push(callback);
    ```

3. This returns an object with an `unsubscribe` method, which removes the associated callback from the array of listeners for a specific event if it is present.

    ```
    return {
        unsubscribe: () => {
            const index = listeners.indexOf(callback);
            if(index !== -1) {
                listeners.splice(index, 1)
            }
        }
    };
    ```

4. This emits an event by executing all callback functions associated with the specified event name, passing optional arguments, and returning an array of results. If there are no callbacks for the event, it returns an empty array.

    ```
    /**
     * @param {string} eventName
     * @param {Array} args
     * @return {Array}
     */
    emit(eventName, args = []) {
        if(!this.events.has(eventName)) {
            return []
        }
        
        const listeners = this.events.get(eventName);
        const results = []
        
        for (const listener of listeners) {
            results.push(listener(...args))
        }
        
        return results;
    }
    ```

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of listeners for the given event. This is because the code iterates over all the listeners and calls each one.

- Space complexity: $O(1)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
This is because the function only involves creating a new array to store the results.

# Code
```
class EventEmitter {
    constructor() {
        this.events = new Map();
    }
    
    /**
     * @param {string} eventName
     * @param {Function} callback
     * @return {Object}
     */
	subscribe(eventName, callback) {
        if(!this.events.has(eventName)) {
            this.events.set(eventName, [])
        }
        const listeners = this.events.get(eventName);
        listeners.push(callback);

		return {
            unsubscribe: () => {
                const index = listeners.indexOf(callback);
                if(index !== -1) {
                    listeners.splice(index, 1)
                }
			}
		};
	}
    
    /**
     * @param {string} eventName
     * @param {Array} args
     * @return {Array}
     */
	emit(eventName, args = []) {
        if(!this.events.has(eventName)) {
            return []
        }
        
        const listeners = this.events.get(eventName);

        const results = []

        for (const listener of listeners) {
            results.push(listener(...args))
        }
		return results;
	}
}
```
