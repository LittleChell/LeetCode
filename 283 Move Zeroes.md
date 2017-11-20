### 283		Move Zeroes

	class Solution(object):
    def moveZeroes(self, nums):
        """
        :type nums: List[int]
        :rtype: void Do not return anything, modify nums in-place instead.
        """
        i = 0
        count = 0
        while i < len(nums):
        	if nums[i] == 0:
        		del nums[i]
        		count += 1
        	else:
        		i += 1
        nums.extend([0]*count)
