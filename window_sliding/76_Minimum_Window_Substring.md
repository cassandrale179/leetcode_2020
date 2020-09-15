

# 76. Minimum Window Substring

## Problem Statement
Given a string S and a string T, find the minimum window in S which will contain all the characters in T in complexity O(n).

Example:
```
Input: S = "ADOBECODEBANC", T = "ABC"
Output: "BANC"
```
Note:

If there is no such window in S that covers all characters in T, return the empty string "".
If there is such window, you are guaranteed that there will always be only one unique minimum window in S.

## Solution
```python
from collections import Counter 
class Solution(object):
    
    # 1. Return true if substring contains all char in s2 
    def validate(self, s1, t): 
        d1 = Counter(s1)
        d2 = Counter(t)
        for key in d2: 
            if d1[key] < d2[key]:
                return False
        return True
                
    # 2. Main function
    def minWindow(self, s, t):
        left, right = 0, 0 
        ans = ""
        while right < len(s)+1:
            substr = s[left:right]  
            while self.validate(substr, t):
                if ans == "" or len(substr) < len(ans): 
                    ans = substr
                left += 1  
                substr = s[left:right]  
            right += 1  
        return ans
 ```
