### 350	Intersection of Two Arrays II

	"使用了collections模块的Counter函数"

	Counter函数目的是用来跟踪值出现的次数,它是一个无序的容器类型，以字典的键值对形式存储，其中元素作为key，其计数作为value

	+、-、&、|操作也可以用于Counter。其中&和|操作分别返回两个Counter对象各元素的最小值和最大值。需要注意的是，得到的Counter对象将删除小于1的元素。

	class Solution(object):
    def intersect(self, nums1, nums2):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        :rtype: List[int]
        """
        import collections
        C = collections.Counter
        return list((C(nums1) & C(nums2)).elements())
