### 27		Remove Element

	删除数组中给定的所有相等值

	class Solution(object):
    def removeElement(self, nums, val):
        """
        :type nums: List[int]
        :type val: int
        :rtype: int
        """
        i=0
        while i < len(nums):
        	if nums[i] == val:	del nums[i]
        	else:	i += 1
        return len(nums)
