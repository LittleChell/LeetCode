### 172	Factorial Trailing Zeroes

	Because all trailing 0 is from factors 5 * 2.
	But sometimes one number may have several 5 factors, for example, 25 have two 5 factors, 125 have three 5 factors. In the n! operation, factors 2 is always ample. So we just count how many 5 factors in all number from 1 to n.
	5的个数即是零的个数。
	[5,25)中有一个5，[25,125)中有2个5，[125,625)中有3个5，依次类推

	class Solution(object):
    def trailingZeroes(self, n):
        """
        :type n: int
        :rtype: int
        """
        count = 0
        while n//5 > 0:
        	count += n//5
        	n //= 5
        return count
