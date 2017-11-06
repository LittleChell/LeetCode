### 136	Single Number

	class Solution(object):
    def singleNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        res = nums[0]
        for num in nums[1:]:
        	res ^= num
        return res

---

	class Solution(object):
    def singleNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        dic = {}
        for i in range(len(nums)):
        	if not dic.get(nums[i]):
        		dic[nums[i]] = 1
        	else: del dic[nums[i]]
        return list(dic.keys())[0]

---

	
