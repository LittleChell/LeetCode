### 11		Container With Most Water

	
	
	"""
	# 指定初始的时候两端l, r组成的容积最大，可以假设l的高度小于r
    # 往lr里面搜寻，而且必须是高度更低的l向里面搜寻（r往里面搜寻没有意义，容积肯定是小于lr组合的）
    # 假设里面有容积更大的m，m必然高度高于l且是mr组合，这时候更新l->m
	#以此类推
	"""

	最清晰版本

	class Solution(object):
    def maxArea(self, height):
        """
        :type height: List[int]
        :rtype: int
        """
        # 指定初始的时候两端l, r组成的容积最大，可以假设l的高度小于r
        # 往lr里面搜寻，而且必须是高度更低的l向里面搜寻（r往里面搜寻没有意义，容积肯定是小于lr组合的）
        # 假设里面有容积更大的m，m必然高度高于l且是mr组合，这时候更新l->m
        
        l, r = 0, len(height)-1
        m, n = l, r
        area = 0
        while l < r:
        	if height[l] <= height[r]:
        		area = max(area, (r-l)*height[l])
        		l += 1
        	else:
        		area = max(area, (r-l)*height[r])
        		r -= 1
        return area

-----------------------------------------------


	"""
	高度更高时才比较面积大小
	"""

	class Solution(object):
    def maxArea(self, height):
        """
        :type height: List[int]
        :rtype: int
        """
        l, r = 0, len(height)-1
        area = (r-l)*min(height[r], height[l])
        m, n = l, r
        while m < n-1:
        	if height[l] <= height[r]:
        		m += 1
        		if height[m] > height[l]:
        			l = m
        			area = max(area, (r-l)*min(height[r], height[l]))
        	else:
        		n -= 1
        		if height[n] > height[r]:
        			r = n
        			area = max(area, (r-l)*min(height[r], height[l]))
        return area

----------------------------------------------------------
	
	"""
	简化版
	"""

	class Solution(object):
    def maxArea(self, height):
        """
        :type height: List[int]
        :rtype: int
        """
        
        l, r = 0, len(height)-1
        area = (r-l)*min(height[r], height[l])
        while l < r:
        	if height[l] <= height[r]:
        		l += 1
        	else:
        		r -= 1
        	area = max(area, (r-l)*min(height[r], height[l]))
        return area
