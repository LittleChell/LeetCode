### 198	House Robber

	“偷第n家不偷第n-1家且前n-2家尽量多的偷”和“不偷第n家且前n-1家尽量多的偷”
	nums[i]存放的是该位置之前（包含该位置）所能偷到的最多的钱
	nums[i] = max(nums[i-2]+num[i], nums[i-1])

	class Solution(object):
    def rob(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        if not nums: return 0
        if len(nums) == 1:	return nums[0]
        if len(nums) == 2:	return max(nums[0], nums[1])
        i = 2
        nums[1] = max(nums[0], nums[1])
        while i < len(nums):
        	nums[i] = max(nums[i] + nums[i-2], nums[i-1])
        	i += 1
        return nums[i-1]
