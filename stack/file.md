# 946. Validate Stack Sequences 

Given two sequences pushed and popped with distinct values, return true if and only if this could have been the result of a sequence of push and pop operations on an initially empty stack.

 
## Input 
```
Example 1:
Input: pushed = [1,2,3,4,5], popped = [4,5,3,2,1]
Output: true
Explanation: We might do the following sequence:
push(1), push(2), push(3), push(4), pop() -> 4,
push(5), pop() -> 5, pop() -> 3, pop() -> 2, pop() -> 1
```
```
Example 2:
Input: pushed = [1,2,3,4,5], popped = [4,3,5,1,2]
Output: false
Explanation: 1 cannot be popped before 2.
```

## Code 
```python
class Solution(object):
    def validateStackSequences(self, pushed, popped):
        stack = []
        for i in pushed:
            stack.append(i)  
            while stack and popped and popped[0] == stack[-1]:
                stack.pop()
                popped.pop(0)
        return not stack
 ```
