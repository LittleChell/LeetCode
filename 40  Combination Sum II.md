### 40		Combination Sum II

	"""
	和Combination Sum相比只是不能重复使用相同的字符，因此下一次开始的位置从后面一位开始。
	"""

	class Solution(object):
    def combinationSum2(self, candidates, target):
        """
        :type candidates: List[int]
        :type target: int
        :rtype: List[List[int]]
        """
        newList = sorted(candidates)
        result = []
        index = 0
        def dps(currList, remain, index):
        	for i in range(index, len(newList)):
        		if newList[i] > remain: return
        		elif remain-newList[i] == 0:
        			tempList = currList+[newList[i]]
        			if not tempList in result:
        				result.append(tempList)
        				return 
        		dps(currList+[newList[i]], remain-newList[i], i+1)
        dps([], target, 0)

        return result