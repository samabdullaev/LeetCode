# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->

##### Good to know:

1. 
2. 
3. 

# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity:
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity:
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        frequency = {}
        
        for num in nums:
            if num not in frequency:
                frequency[num] = 1
            else:
                frequency[num] = frequency[num] + 1
        
        frequency = dict(sorted(frequency.items(), key=lambda x: x[1], reverse=True))
        result = list(frequency.keys())[:k]
        return result
```
