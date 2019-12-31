# Palindrome Partitioning
```python3
Given a string s, partition s such that every substring of the partition is a palindrome.

Return all possible palindrome partitioning of s.

Example:

Input: "aab"
Output:
[
  ["aa","b"],
  ["a","a","b"]
]
```
🎉 Answer
```python3
class Solution:
    def partition(self, s: str) -> List[List[str]]:
        def helper(input_string, path, total_length):
            if total_length == len(s):
                res.append(path)
                return
            for i in range(len(input_string)+1):
                if self.is_palindrome(input_string[:i]):
                    helper(input_string[i:], path + [input_string[:i]], total_length + len(input_string[:i]))
                    
        res = []
        helper(s, [], 0)
        return res
        
        
    def is_palindrome(self, s):
        if len(s) == 0:
            return False
        if len(s) == 1:
            return True
        half_length = len(s)//2
        for i in range(half_length):
            if s[i] != s[~i]:
                return False
        return True
```
