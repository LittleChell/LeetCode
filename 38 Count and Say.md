### 38	Count and Say

	class Solution(object):
    def countAndSay(self, n):
        """
        :type n: int
        :rtype: str
        """
        if n == 1:	return '1'

        if n == 2:	return '11'

        # 取得某个数字的count and say
        def getCountAndSay(nums):
            nums = str(nums)
            preNum = nums[0]
            partRst = ''
            count = 1
            for i in range(1, len(nums)):
                if nums[i] == preNum:
                    count += 1
                else:
                    partRst += str(count) + str(nums[i-1])
                    preNum = nums[i]
                    count = 1
            else:
                partRst += str(count) + str(nums[i])
            return partRst
			
        i = 2
        tarN = 11

        while i < n:
	        tarN = getCountAndSay( tarN )
	        i += 1

        return tarN