### 39		Combination Sum

	"""
	Discussion里面基本都是需要先按升序排好序，再进行操作。
	这里使用了深度优先算法。
	排序后，使用target减去第一项得到remain，然后剩下的依然可以从第一项到后面小于remian之间的项数里面加入到可能存在的结果数组currList里面，如此迭代下去。迭代完第一项的所有可能再迭代第二项的所有可能，直到找到所有的解。
	"""

	class Solution(object):
    def combinationSum(self, candidates, target):
        """
        :type candidates: List[int]
        :type target: int
        :rtype: List[List[int]]
        """

        
        def dfs(remain, currList, index):
        	if remain == 0:
        		result.append(currList)
        		return 
        	for i in range(index, len(sortList)):
        		if sortList[i] > remain: break
        		dfs(remain - sortList[i], currList+[sortList[i]], i)
        		
        result = []
        sortList = sorted(candidates)
        dfs(target, [], 0)
        return result
