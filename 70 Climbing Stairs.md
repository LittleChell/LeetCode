### 70		Climbing Stairs

	"""
	踏上第n级可以由第n-1级踏一级和第n-2级踏两级，即
	f(n)=f(n-1)+f(n-2)
	是一个Fibonacci数列
	"""
	steps		1	2	3	4	5	6
	methods	1	1	2	3	5	8	13

	class Solution(object):
    def climbStairs(self, n):
        """
        :type n: int
        :rtype: int
        """
        a, b = 0, 1
        for i in range(n):
            a, b = b, a + b
        return b

------------------------------------------------------

	超时(递归)
	class Solution(object):
    def climbStairs(self, n):
        """
        :type n: int
        :rtype: int
        """
        def getStairs(n):
        	if n == 1:	return 1
        	if n == 2:	return 2
        	nums1 = getStairs(n-1)
        	nums2 = getStairs(n-2)
        	return nums1 + nums2
        return getStairs(n)