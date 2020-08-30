# Letter Combinations of a Phone Number
```
Given a string containing digits from 2-9 inclusive, 
return all possible letter combinations that the number could represent.

A mapping of digit to letters (just like on the telephone buttons) is given below. 
Note that 1 does not map to any letters.

Try to use backtrack, dfs and recursive methods to solve this problem

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/letter-combinations-of-a-phone-number
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。
```
🎉 Answer
## backtrack
```python3
class Solution:
    correspond_dict = {
        '2': ['a', 'b', 'c'],
        '3': ['d', 'e', 'f'],
        '4': ['g', 'h', 'i'],
        '5': ['j', 'k', 'l'],
        '6': ['m', 'n', 'o'],
        '7': ['p', 'q', 'r', 's'],
        '8': ['t', 'u', 'v'],
        '9': ['w', 'x', 'y', 'z']
    }
    def letterCombinations(self, digits: str) -> List[str]:
        if not digits:
            return []
        res = []
        global_list = []
        def back_track(remaining_digits):
            if not remaining_digits:
                res.append("".join(global_list))
                return

            for sig in self.correspond_dict[remaining_digits[0]]:
                # print(f"gl: {global_list}, append: {sig}")
                global_list.append(sig)
                back_track(remaining_digits[1:])
                global_list.pop()

        back_track(digits)
        return res
```
## dfs
```python3
class Solution:
    correspond_dict = {
        '2': ['a', 'b', 'c'],
        '3': ['d', 'e', 'f'],
        '4': ['g', 'h', 'i'],
        '5': ['j', 'k', 'l'],
        '6': ['m', 'n', 'o'],
        '7': ['p', 'q', 'r', 's'],
        '8': ['t', 'u', 'v'],
        '9': ['w', 'x', 'y', 'z']
    }
    def letterCombinations(self, digits: str) -> List[str]:
        if not digits:
            return []
        res = []
        def dfs(remaining_digits, current_list):
            if not remaining_digits:
                res.append("".join(current_list))
                return

            for sig in self.correspond_dict[remaining_digits[0]]:
                dfs(remaining_digits[1:], current_list + [sig])

        dfs(digits, [])
        return res         
```
## recursion
```python3
class Solution:
    correspond_dict = {
        '2': ['a', 'b', 'c'],
        '3': ['d', 'e', 'f'],
        '4': ['g', 'h', 'i'],
        '5': ['j', 'k', 'l'],
        '6': ['m', 'n', 'o'],
        '7': ['p', 'q', 'r', 's'],
        '8': ['t', 'u', 'v'],
        '9': ['w', 'x', 'y', 'z']
    }
    def letterCombinations(self, digits: str) -> List[str]:
        if len(digits) == 0:
            return []
        current_list = self.correspond_dict[digits[-1]]
        if len(digits) == 1:
            return current_list
        previous_combination = self.letterCombinations(digits[:-1])
        new_res = []
        for sig in previous_combination: # outer loop 4^(n-1)
            for new_char in current_list: # inner loop 4
                new_res.append(sig + new_char)
        return new_res
    # T(n) = T(n-1) + 4^(n-1) * 4 = T(n-1) + 4^n
    # T(n) = O(n*4^n) 
```
