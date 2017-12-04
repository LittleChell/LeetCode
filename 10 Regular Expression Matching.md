### 10		Regular Expression Matching

	"""
	分析：本题使用DP（动态规划）算法
	以isMatch("aaa", "ab*a*c*a")为例，使用矩阵来演示
	s代表"aaa"，p代表"ab*a*c*a"，利用s匹配p
	s为x轴，p为y轴建立坐标系，两者下标都是从1开始。dp用来存储坐标状态，从[0][0]开始;dp[i][j]代表s[:i]和p[:j]匹配，dp的两个下标均比s、p大1。
	
	1、初始状态： x代表不成立，!代表成立。初始s[]与p[]是匹配的，故(0,0)是true
		√(0,0)	x x x
				a a a
			 ----------x轴
		x	a|	x x x
		x	b|  x x x
		x	*|  x x x
		x	a|  x x x
		x	*|  x x x
		x	c|  x x x
		x	*|  x x x
		x	a|  x x x
			 |
			 y轴		
	2、更新特殊情况，即s==[]但是p不为空
		从p的j>=1开始
		if(p.charAt(i) == '*'){
			dp[0][j+1]=dp[0][j-1]
		}
		√(0,0)	x x x
				a a a
			 ----------x轴
		x	a|	x x x
		x	b|  x x x
		x	*|  x x x
		x	a|  x x x
		x	*|  x x x
		x	c|  x x x
		x	*|  x x x
		x	a|  x x x
			 |
			 y轴		
	3、
	1, If p.charAt(j) == s.charAt(i) :  dp[i+1][j+1] = dp[i][j];
	2, If p.charAt(j) == '.' : dp[i+1][j+1] = dp[i][j];
	3, If p.charAt(j) == '*': 
	   here are two sub conditions:
	               1   if p.charAt(j-1) != s.charAt(i) : dp[i+1][j+1] = dp[i+1][j-1]  //in this case, a* only counts as empty
	               2   if p.charAt(i-1) == s.charAt(i) or p.charAt(i-1) == '.':
	                              dp[i+1][j+1] = dp[i][j+1]    //in this case, a* counts as multiple a 当前s[i]向左边s[i-1]看齐，说明*匹配多个a
	                           or dp[i+1][j+1] = dp[i+1][j]   // in this case, a* counts as single a这里说明*匹配一个a，虽然此时也有dp[i+1][j+1] = dp[i][j+1]，但是从少的原则上说先匹配一个
	                           or dp[i+1][j+1] = dp[i+1][j-1]   // in this case, a* counts as empty这里*的作用就是省略掉前面的匹配项
	√(0,0)	x x x
				a a a
			 ----------x轴
		x	a|	√ x x
		x	b|  x x x
		x	*|  √ x x
		x	a|  x √ x
		x	*|  √ √ x
		x	c|  x x x
		x	*|  √ x x
		x	a|  x x x
			 |
			 y轴	
	
	注意：isMatch("aaaa", "a*aa")中a*是可以匹配0个或多个
	"""

	class Solution(object):
    def isMatch(self, s, p):
        """
        :type s: str
        :type p: str
        :rtype: bool
        """
		#初始化dp
        dp = [ [False]*(len(p)+1) for _ in range(len(s)+1) ]
        dp[0][0] = True
		#更新特殊情况s为空但p不为空
        i = 1
        while i < len(p):
        	if p[i] == '*':
        		dp[0][i+1] = dp[0][i-1]
        	i += 1
		#正常情况
        for x in range(len(s)):
        	for y in range(len(p)):
        		if p[y] == s[x] or p[y] == '.':
        			dp[x+1][y+1] = dp[x][y]
        		elif p[y] == '*':
        			if p[y-1] != s[x] and p[y-1] != '.':
        				dp[x+1][y+1] = dp[x+1][y-1]
        			else:
        				dp[x+1][y+1] = (dp[x+1][y] or dp[x][y+1] or dp[x+1][y-1])

        return dp[len(s)][len(p)]