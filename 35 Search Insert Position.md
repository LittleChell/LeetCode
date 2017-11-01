### 35	Search Insert Position

	class Solution(object):
    def searchInsert(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: int
        """
        if not nums:	return 0

        if nums[0] >= target: return 0

        if nums[-1] < target: return len(nums)

        nowPointer, prePointer, surPointer = 0, 0, len(nums)-1

        while (prePointer + 1 != surPointer):
        	if target > nums[(prePointer + surPointer) // 2]:	prePointer = (prePointer + surPointer) // 2
        	elif target < nums[(prePointer + surPointer) // 2]:	surPointer = (prePointer + surPointer) // 2
        	else: return (prePointer + surPointer) // 2
        	# print(prePointer, surPointer)
        if nums[prePointer] == target:	return prePointer
        if nums[surPointer] == target:	return surPointer
        return prePointer + 1