### 204		Count Primes

	"""
	给定n，计算n前面（不包括n）的所有质数个数有多少个。
	思路：划去2所有的倍数，然后划去3所有的倍数，下一个没有被划去的是5，然后划去5的所有倍数，依次类推。
	只需计算到m使m^2<n and (m+1)^2>=n即可。因为两数相乘，两数越相近乘积越大，比如(2x8)<(5x5)
	"""

	class Solution(object):
    def countPrimes(self, n):
        """
        :type n: int
        :rtype: int
        """
        if n <= 2:
            return 0
        elif n == 3:
        	return 1
        dicts = [True]*n
        count = n-2
        i = 2
        while i*i < n:
        	j = 2
        	while j*i < n:
        		if not dicts[j*i]:
	        		j += 1
        			continue
        		dicts[j*i] = False
        		count -= 1
        		j += 1
        	i += 1
        return count
