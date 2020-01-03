# Majority Element
```python3
Given an array of size n, find the majority element. The majority element is the element that appears more than ⌊ n/2 ⌋ times.

You may assume that the array is non-empty and the majority element always exist in the array.

Example 1:

Input: [3,2,3]
Output: 3
Example 2:

Input: [2,2,1,1,1,2,2]
Output: 2
```

🎉 Answer 1
```python3
class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        collect = collections.Counter(nums)
        return sorted(collect.items(), key=lambda x:x[1])[-1][0]
```

🎉 Answer 2
```python3
class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        counter, target = 0, nums[0]
        for i in range(len(nums)):
            if counter == 0:
                counter = 1
                target = nums[i]
            elif target == nums[i]:
                counter +=1
            else:
                counter -=1
        return target
```
