### 69	Sqrt(x)

	class Solution(object):
    def mySqrt(self, x):
        """
        :type x: int
        :rtype: int
        """
        l, m, r = 0, x//2, x
        if x == 1:	return 1;
        while not (m**2 <= x and (m+1)**2 > x):
        	# if m**2 <= x and (m+1)**2 > x:
        	if m**2 < x:
        		l = m
        		m = (l+r)//2
        	elif m**2 > x:
        		r = m
        		m = (l+r)//2
        return m

---
	class Solution(object):
    def mySqrt(self, x):
        """
        :type x: int
        :rtype: int
        """
        import math
        return int(math.floor(math.sqrt(x)))