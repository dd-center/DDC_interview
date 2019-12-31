# Generate Parentheses
```python3
Given n pairs of parentheses, write a function to generate all combinations of well-formed parentheses.

For example, given n = 3, a solution set is:

[
  "((()))",
  "(()())",
  "(())()",
  "()(())",
  "()()()"
]
```
🎉 Answer:
```python3
class Solution:
    def generateParenthesis(self, n: int) -> List[str]:
        if n==0:
            return ""
        def helper(left, right, path):
            if left==0 and right==0:
                res.append(path)
                return
            if left > right:
                return
            
            if left > 0:
                helper(left-1, right, path+'(')
            if right > 0:
                helper(left, right-1, path+')')
                
        res = []
        helper(n, n, "")
        return res
```
