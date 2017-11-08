### 263		Ugly Number

	"""
	只能整除2、3、5，整除完2、3、5后如果不是1，那肯定包含有其它大于1的数字
	"""

	class Solution(object):
    def isUgly(self, num):
        """
        :type num: int
        :rtype: bool
        """
        if num <= 0:	return False
        while num%2 == 0:
        	num /= 2
        while num%3 == 0:
        	num /= 3
        while num%5 == 0:
        	num /= 5
        if num != 1:	return False
        return True

------------------------------------------------------

	优化
	class Solution(object):
    def isUgly(self, num):
        """
        :type num: int
        :rtype: bool
        """
        if num <= 0:	return False
        while num%2 == 0:
        	num /= 2
        while num%3 == 0:
        	num /= 3
        while num%5 == 0:
        	num /= 5
        if num != 1:	return False
        return True