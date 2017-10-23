### 9	Palindrome Number   

	class Solution(object):
	    def isPalindrome(self, x):
	        """
	        :type x: int
	        :rtype: bool
	        """
	        
	        def getIntLen(num):
	        	baseLen = 1
	        	num = abs(num)
	        	while True:
	        		if num//(10**baseLen) == 0:
	        			return baseLen
	        		baseLen += 1
	
	        lenX = getIntLen(x)
	        halfK = lenX//2
	        if x < 0	return False
	        if lenX == 0:	return False
	        if lenX == 1:	return True
	        leftK = halfK*2 if getIntLen(x)%2 == 1 else halfK*2-1
	        while halfK > 0:
	        	if x // 10**(leftK) != x%10:
	        		return False
	        	x = (x%10**(leftK))//10
	        	halfK -= 1
	        	leftK -= 2
	        return True
