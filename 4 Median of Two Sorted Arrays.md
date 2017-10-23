### 4 Median of Two Sorted Arrays  

	class Solution:
	    def findMedianSortedArrays(self, nums1, nums2):
	        totalLength = len(nums1) + len(nums2)
	        if totalLength%2 == 0:
	            return (self.getK(nums1, nums2, totalLength//2 - 1) + self.getK(nums1, nums2, totalLength//2))/2
	        else:
	            return self.getK(nums1, nums2, totalLength//2)
	
	    def getK(self, nums1, nums2, k):
	        index1, index2 = 0, 0
	        len1, len2 = len(nums1), len(nums2)
	        getItem = 0
	        cpK = k
	        if len1 and len2:
	            while k >= 0:
	                if (len1) == index1:
	                    getItem = nums2[cpK-len1]
	                    break
	                if (len2) == index2:
	                    getItem = nums1[cpK-len2]
	                    break
	                if( nums1[index1] >= nums2[index2] ):
	                    getItem = nums2[index2]
	                    index2 += 1
	                else:
	                    getItem = nums1[index1]
	                    index1 += 1
	                k -= 1
	        elif len1:
	            getItem = nums1[k]
	        elif len2:
	            getItem = nums2[k]
	        else:
	            getItem = False
	
	        return getItem
