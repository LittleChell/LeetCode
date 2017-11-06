### 66	Plus One

	class Solution(object):
    def plusOne(self, digits):
        """
        :type digits: List[int]
        :rtype: List[int]
        """
        i = len(digits) - 1
        digits[i] += 1 
        carry = 0
        while i >= 0:
        	if carry + digits[i] >= 10:
        		carry = 1
        		digits[i] = 0
        	else:
        		digits[i] += carry
        		carry = 0
        		break
        	i -= 1
        if carry:
        	digits = [1] + digits
        return digits