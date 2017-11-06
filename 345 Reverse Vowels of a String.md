### 345	Reverse Vowels of a String

	翻转元音项

	class Solution(object):
    def reverseVowels(self, s):
        """
        :type s: str
        :rtype: str
        """
        dic = "aeiouAEIOU"
        start, end = 0, len(s)-1
        s = list(s)
        while start < end:
        	while s[start] not in dic and start < end:
        		start += 1
        	while s[end] not in dic and start < end:
        		end -= 1
        	s[start], s[end] = s[end], s[start]
        	start += 1
        	end -= 1
        return ''.join(s)
