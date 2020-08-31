# Maximum subarray
```
Given an integer array nums, 
find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/maximum-subarray
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。
```
🎉 Answer

## divide & conquer
```python3
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        'try divide & conquer'
        if not nums:
            return float('-inf')

        middle_index = len(nums)//2
        left_max = self.maxSubArray(nums[:middle_index])
        right_max = self.maxSubArray(nums[middle_index+1:])
        'start at middle_index'
        contained_left_max, contained_right_max = 0, 0
        tmp_sum = 0
        for i in reversed(range(middle_index)):
            tmp_sum += nums[i]
            contained_left_max = max(contained_left_max, tmp_sum)
            
        tmp_sum = 0
        for i in range(middle_index+1, len(nums)):
            tmp_sum += nums[i]
            contained_right_max = max(contained_right_max, tmp_sum)

        contained_max = nums[middle_index] + contained_left_max + contained_right_max
        return max(max(left_max, right_max), contained_max)
```

## dp
```python3
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        max_res = -sys.maxsize
        array_sum = 0

        for num in nums:
            if array_sum < 0:
                array_sum = 0
            array_sum += num    
            max_res = max(array_sum, max_res)
        return max_res
```
