# Combination&permutation problems zoo
## Combination
```python3
Given two integers n and k, return all possible combinations of k numbers out of 1 ... n.

Example:

Input: n = 4, k = 2
Output:
[
  [2,4],
  [3,4],
  [2,3],
  [1,2],
  [1,3],
  [1,4],
]
```

🎉 Answer:
```python3
class Solution:
    def combine(self, n: int, k: int) -> List[List[int]]:
        def helper(path, index):
            if len(path) == k:
                res.append(path)
            for i in range(index, n+1):
                helper(path+[i], i+1)
        
        res = []
        helper([], 1)
        return res
```
## Permutations 其一
```python3
Given a collection of distinct integers, return all possible permutations.

Example:

Input: [1,2,3]
Output:
[
  [1,2,3],
  [1,3,2],
  [2,1,3],
  [2,3,1],
  [3,1,2],
  [3,2,1]
]
```

🎉 Answer
```python3
class Solution:
    def permute(self, nums: List[int]) -> List[List[int]]:
        def dfs(path, nums):
            if len(path) == global_length:
                res.append(path)
                return
            for i in range(len(nums)):
                dfs(path + [nums[i]], nums[:i] + nums[i+1:])
        
        res = []
        global_length = len(nums)
        dfs([], nums)
        return res
```

## Permutations 其二
```python3
Given a collection of numbers that might contain duplicates, return all possible unique permutations.

Example:

Input: [1,1,2]
Output:
[
  [1,1,2],
  [1,2,1],
  [2,1,1]
]
```
🎉 Answer
```python3
class Solution:
    def permuteUnique(self, nums: List[int]) -> List[List[int]]:
        def dfs(path):
            if len(path) == len(nums):
                res.append(path)
                return
            for i in range(len(nums)):
                if not visited[i]:
                    if i > 0 and visited[i-1] and nums[i] == nums[i-1]:
                        continue
                    visited[i] = True
                    dfs(path + [nums[i]])
                    visited[i] = False
            
        nums.sort()
        res = []
        visited = [False]*len(nums)
        dfs([])
        return res
```
## Subsets 其一
```python3
Given a set of distinct integers, nums, return all possible subsets (the power set).

Note: The solution set must not contain duplicate subsets.

Example:

Input: nums = [1,2,3]
Output:
[
  [3],
  [1],
  [2],
  [1,2,3],
  [1,3],
  [2,3],
  [1,2],
  []
]
```
🎉 Answer
```python3
class Solution:
    def subsets(self, nums: List[int]) -> List[List[int]]:
        def dfs(path, index):
            res.append(path)
            for i in range(index, len(nums)):
                dfs(path + [nums[i]], i+1)

        res = []
        dfs([], 0)
        return res
```

## Subsets 其二
```python3
Given a collection of integers that might contain duplicates, nums, return all possible subsets (the power set).

Note: The solution set must not contain duplicate subsets.

Example:

Input: [1,2,2]
Output:
[
  [2],
  [1],
  [1,2,2],
  [2,2],
  [1,2],
  []
]
```
🎉 Answer
```python3
class Solution:
    def subsetsWithDup(self, nums: List[int]) -> List[List[int]]:
        def dfs(path, index):
            res.append(path)
            for i in range(index, len(nums)):
                if i>index and nums[i-1] == nums[i]:
                    continue
                dfs(path + [nums[i]], i+1)
                
        nums.sort()
        res = []
        dfs([], 0)
        return res
```
## Combination Sum 其一
```python3
Given a set of candidate numbers (candidates) (without duplicates) and a target number (target), find all unique combinations in candidates where the candidate numbers sums to target.

The same repeated number may be chosen from candidates unlimited number of times.

Note:

All numbers (including target) will be positive integers.
The solution set must not contain duplicate combinations.
Example 1:

Input: candidates = [2,3,6,7], target = 7,
A solution set is:
[
  [7],
  [2,2,3]
]
Example 2:

Input: candidates = [2,3,5], target = 8,
A solution set is:
[
  [2,2,2,2],
  [2,3,3],
  [3,5]
]
```
🎉 Answer
```python3
class Solution:
    def combinationSum(self, candidates: List[int], target: int) -> List[List[int]]:
        def dfs(target, path, index):
            if target == 0:
                res.append(path)
                return
            if target < 0:
                return
            for i in range(index, len(candidates)):
                dfs(target-candidates[i], path + [candidates[i]], i)
        
        res = []
        dfs(target, [], 0)
        return res
```



### A following question:
How would you change your program if you wanna output duplicate combinations?
```python3
Example 1:

Input: candidates = [2,3,6,7], target = 7,
A solution set is:
[
  [2,2,3],
  [2,3,2],
  [3,2,2],
  [7]
]

Example 2:

Input: candidates = [2,3,5], target = 8,
A solution set is:
[
  [2,2,2,2],
  [2,3,3],
  [3,2,3],
  [3,3,2],
  [3,5],
  [5,3]
]
```
🎉 Answer
```python3
class Solution:
    def combinationSum(self, candidates: List[int], target: int) -> List[List[int]]:
        def dfs(target, path):
            if target == 0:
                res.append(path)
                return
            if target < 0:
                return
            for i in range(len(candidates)):
                dfs(target-candidates[i], path + [candidates[i]])
        
        res = []
        dfs(target, [])
        return res
```
## Combination Sum 其二
```python3
Given a collection of candidate numbers (candidates) and a target number (target), find all unique combinations in candidates where the candidate numbers sums to target.

Each number in candidates may only be used once in the combination.

Note:

All numbers (including target) will be positive integers.
The solution set must not contain duplicate combinations.
Example 1:

Input: candidates = [10,1,2,7,6,1,5], target = 8,
A solution set is:
[
  [1, 7],
  [1, 2, 5],
  [2, 6],
  [1, 1, 6]
]
Example 2:

Input: candidates = [2,5,2,1,2], target = 5,
A solution set is:
[
  [1,2,2],
  [5]
]
```
🎉 Answer
```python3
class Solution:
    def combinationSum2(self, candidates: List[int], target: int) -> List[List[int]]:
        def dfs(path, index, target):
            if target == 0:
                res.append(path)
                return
            if target < 0:
                return
            for i in range(index, len(candidates)):
                if i > index and candidates[i-1] == candidates[i]:
                        continue
                dfs(path + [candidates[i]], i+1, target-candidates[i])
        
        res = []
        candidates.sort()
        dfs([], 0, target)
        return res
```
## 技 术 总 结
* 对于要求输出先后顺序的题目，应该用index方法来解决，如Subsets，Combination Sum
* index: i 和 i+1: 如果可以重复利用nums，则使用i，否则使用i+1, 可以对比Subsets和Combination Sum
* 对于不要求输出先后顺序的题目，应该用nums[:i]+nums[i+1:]或visited array来解决。如permutation








