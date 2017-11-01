### 58	Length of Last Word

	class Solution(object):
    def lengthOfLastWord(self, s):
        """
        :type s: str
        :rtype: int
        """
        count = 0
        i = len(s) - 1
        while i >= 0:
        	if s[i] != " ":
        		count += 1
        	elif count:
        		return count
        	i -= 1
        return count