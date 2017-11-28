### 43		Multiply Strings

	"""
	以字符串形式给两个正整数，以字符串形式返回乘积。
	按照手写乘法运算的方法执行即可
	"""

	class Solution(object):
    def multiply(self, num1, num2):
        """
        :type num1: str
        :type num2: str
        :rtype: str
        """
        product = carry = 0
        for i in num1[::-1]:
        	product += int(num2)*int(i)*10**carry
        	carry += 1
        return str(product)
