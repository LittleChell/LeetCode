### 179		Largest Number

	class Solution:
    # @param {integer[]} nums
    # @return {string}
    def largestNumber(self, nums):
        sortedListS = sorted(map(str,nums), key=lambda x:1-float(x)/(10**len(x)-1))
    	# str(int)是为了防止出现"00"
    	sortedListS = str(int("".join(sortedListS)))
    	return sortedListS