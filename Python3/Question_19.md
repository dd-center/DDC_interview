# Edit Distance

```
Given two words word1 and word2, 
find the minimum number of operations required to convert word1 to word2.

You have the following 3 operations permitted on a word:

1. Insert a character
2. Delete a character
3. Replace a character

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/edit-distance
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

经 典 动 态 规 划 问 题
```
🎉 Answer
```python3
class Solution:
    def minDistance(self, word1: str, word2: str) -> int:
        dp = [[0] * (len(word1) + 1) for _ in range(len(word2) + 1)]
        'initialize corner case'
        for i in range(len(word2) + 1):
            dp[i][0] = i

        for j in range(len(word1) + 1):
            dp[0][j] = j    

        for i in range(1, len(word2) + 1):
            for j in range(1, len(word1) + 1):
                dp[i][j] = min(dp[i-1][j-1] if word1[j-1] == word2[i-1] else dp[i-1][j-1] + 1 ,min(dp[i][j-1] + 1, dp[i-1][j] + 1))
        return dp[-1][-1]
```
