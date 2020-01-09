# Binary search
```
Write code to do a binary search
```
🎉 Answer
```python3
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        low, high = 0, len(nums)-1
        
        while low <= high:
            mid = low + (high - low)//2
            if nums[mid] == target:
                return mid
            elif nums[mid] > target:
                high -= 1
            elif nums[mid] < target:
                low += 1
        return -1
```
