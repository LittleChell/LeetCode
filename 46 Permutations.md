### 46		Permutations

	"""
	使用A排序，不用C选择排序。
	1、选择一个元素
	2、在这个元素两边空位都可以放下一个元素
	3、两个元素的三个空位都可以放置下一个元素
	4、一次类推
	"""

	class Solution(object):
    def permute(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        rst = [[]]
        for i, el in enumerate(nums):
        	innerList = []
			#遍历当前的已经局部排好顺序的列表
        	for items in rst:
				#n个元素的n+1个位置都可以放置该元素
        		for k in range(len(items)+1):
        			part = items[:k] + [el] +items[k:]
        			innerList.append(part)
        		rst = innerList
        return rst
