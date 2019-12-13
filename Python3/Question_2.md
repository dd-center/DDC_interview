Sorted two sum

给一个**已经排序**的整数数组，找到两个数使得他们的和等于一个给定的数target。

你需要实现的函数twoSum需要返回这两个数的下标, 并且第一个下标小于第二个下标。注意这里下标的范围是 1 到 n，不是以 0 开头。

样例
给出 numbers = [2, 7, 11, 15], target = 9, 返回 [1, 2] (注意，不是[0,1]).

```
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        start, end = 0, len(nums)-1
        while start < end:
            if nums[start] + nums[end] == target:
                return [start+1, end+1]
            elif nums[start] + nums[end] < target:
                start += 1
            else:
                end -=1
        return [-1, -1]
```
