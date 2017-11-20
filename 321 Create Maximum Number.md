### 321		Create Maximum Number
	
	1、找出总长度为k的两个子列表的各自最大局部列表
	2、合并这两个列表选取最大值列表
	3、取所有合并后列表中的最大值列表
	
	class Solution(object):
    def maxNumber(self, nums1, nums2, k):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        :type k: int
        :rtype: List[int]
        """
        from functools import reduce
        def pickMaxPartList(l, n):
            fi, lenL = 0, len(l)    #fi: 已找到的数字个数
            startIndex = 0              #startIndex: 开始遍历的位置
            rstL = []
            while fi < n:
                val, index = 0, startIndex
                while index <= lenL-(n-fi):
                    if l[index] > val:
                        val, startIndex = l[index], index + 1
                    index += 1
                rstL.append(val)
                fi += 1
            return rstL
        """
        返回合并后最大的数组
        :type nums1: List[int]
        :type nums2: List[int]
        :rtype: List[int]
        """
        def merge(l1, l2):
            ans = []
            while l1 or l2:
                if l1 > l2:
                    ans += l1[0],
                    l1 = l1[1:]
                else:
                    ans += l2[0],
                    l2 = l2[1:]
            return ans

        len1, len2 = len(nums1), len(nums2)
        res = []
        for x in range(max(0, k - len2), min(k, len1) + 1):
            tmp = merge(pickMaxPartList(nums1, x), pickMaxPartList(nums2, k - x))
            res = max(tmp, res)
        return res

            # print(maxNum)
        return list(map(int, list(str(maxNum))))