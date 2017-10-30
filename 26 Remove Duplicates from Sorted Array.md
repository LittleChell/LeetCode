### 26	Remove Duplicates from Sorted Array

	class Solution(object):
    def removeDuplicates(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        if not nums: return 0
        prevEl = nums[0]
        result = 1
        currIndex = 1
        while currIndex < len(nums):
            if not prevEl == nums[currIndex]:
                prevEl = nums[currIndex]
                nums[result] = nums[currIndex]
                result += 1
            # else:
            currIndex += 1
        return result