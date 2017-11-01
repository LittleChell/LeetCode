### 53	Maximum Subarray

	class Solution:
    def maxSubArray(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        # 最终的子数组必然是连续的
        # 当前数组只有在前面得到的结果是正数情况下才和前面的相加，否则该局部取当前元素即可
        # wholeSum取各个分散的子数组中最大的和值
        wholeSum = tmpSum = nums[0]
        for el in nums[1:]:
        	# 如果取el，则连续部分结束，说明前面的和是负数；取el + tmpSum则表示需延续连续部分的和，前面和是正数
        	tmpSum = max( el, el + tmpSum )

        	wholeSum = max( wholeSum, tmpSum )
        return wholeSum