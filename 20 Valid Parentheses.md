### 20	Valid Parentheses

	class Solution(object):
    def isValid(self, s):
        """
        :type s: str
        :rtype: bool
        """
        if len(s)%2:    return False
        dic = {
            '(': 0,
            ')': 1,
            '[': 2,
            ']': 3,
            '{': 4,
            '}': 5
        }
        stack=[s[0]]
        stackIndex = 0
        for i in range(1, len(s)):
            if stack and dic[stack[stackIndex]]+1 != dic[s[i]]:   
                stack.append(s[i])
                stackIndex += 1
            elif not stack:   
                stack.append(s[i])
                stackIndex += 1
            else :
                stack.pop(); stackIndex -= 1
        if stack:    return False
        return True