### 3		Longest Substring Without Repeating Characters

	"""
	1、找出每个不重复的最长子列表
	2、从所有的子列表中找出长度最长的那个子列表
	"""

	class Solution(object):
    def lengthOfLongestSubstring(self, s):
        maxL = start = i = 0
        l = []
        li = ''
        while i < len(s):
            if s[i] in li:
                maxL = max(maxL, len(li))
                start = s.index(s[i], start)+1
                li = s[start:i+1]
            else:
                li += s[i]
            i += 1
        maxL = max(maxL, len(li))
        return maxL