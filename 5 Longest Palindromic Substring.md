### 5		Longest Palindromic Substring

	1、假设当前最小子字符串str是一个Palindrome(aba or aa)
	2、轮到下一个字母z时，如果str两边分别加上z和右边界的右边一个字母也能组成Palindrome，则更新最小子字符串Palindrome，更新右边界和跨度

	discuss上面的比较多的方式就是下面的方式，意思大致类似，都是遍历一遍str，每个str都找一下Palindrome，然后取最长那一个。
	

	class Solution(object):
    def longestPalindrome(self, s):
        """
        :type s: str
        :rtype: str
        """
        if not s:	return ''
		#r：最小子字符串Palindrome右边界
		#rg：最小子字符串Palindrome跨度
        rg, r = 1, 0
        for i in range(len(s)):
        	# 不能超出范围 i-rg >= 0
        	if i-rg - 1 >= 0 and s[i-rg-1:i+1] == s[i-rg-1:i+1][::-1]:
        		r = i - rg - 1
        		rg += 2
			# 仅适用于abccba型Palindrome找到中间项cc，其它情形都是上面那种情况
        	elif i-rg >= 0 and s[i-rg:i+1] == s[i-rg:i+1][::-1]:
        		r = i-rg
        		rg += 1
        return s[r:r+rg]

---------------------------------------
	
	Time Executive Exceeding
	算法不合理
	找出所有的子项Palindrome然后找到最长长度的那一串

	class Solution(object):
    def longestPalindrome(self, s):
        """
        :type s: str
        :rtype: str
        """
        subl = ''
        dicts = {}
        innerR = innerL = middle = 0
        for i in range(len(s)):
        	if s[i] in dicts:
        		dicts[s[i]].append(i)
        	else:
        		dicts[s[i]] = [i]
        for el in dicts.items():
        	rg = el[1]
        	if len(rg)>=2:
        		for j in range(len(rg)):
	        		start = rg[j]
        			for k in rg[j+1:]:
        				end = k
	        			innerR, innerL = start, end
	        			while (s[innerR] == s[innerL]) & (innerR < innerL):
	        				innerR += 1
	        				innerL -= 1
	        			if innerR >= innerL:
	        				subl = subl if len(subl) > (end+1-start) else s[start:end+1]
        	else:
        		subl = subl if len(subl) > 1 else s[rg[0]]
        return subl
