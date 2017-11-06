### 242	Valid Anagram

	简化为是否每个字母出现次数相同

	class Solution(object):
    def isAnagram(self, s, t):
        """
        :type s: str
        :type t: str
        :rtype: bool
        """
        if sorted(s) == sorted(t):  return True
        return False
