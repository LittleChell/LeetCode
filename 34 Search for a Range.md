### 34		Search for a Range

	"""
	二分法查找，先找到元素，再找元素左右相等的元素
	没找到元素则返回[-1, -1]
	"""

	class Solution(object):
    def searchRange(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        if not nums: return [-1, -1]
        start, end = 0, len(nums)-1
        middle = (start + end)//2
		#找出middle附近相等的值
        def getRL(middle):
        	r = middle-1
        	l = middle+1
        	while r >= 0:
        		if nums[r] != target:	break
        		r -= 1
        	while l < len(nums):
        		if nums[l] != target:	break
        		l += 1
        	return [r+1,l-1]
        # 二分法查找元素，元素是一定存在的，那么肯定能在middle处找到该元素
        while start < end:
        	if nums[middle] > target:
        		end = middle-1
        	elif nums[middle] < target:
        		start = middle+1
        	else:
        		break;
        	middle = (start + end)//2
        if nums[middle] != target:
        	return [-1, -1]
        return getRL(middle)