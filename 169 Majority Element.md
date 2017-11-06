### 169	Majority Element

	class Solution(object):
    def majorityElement(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        return sorted(nums)[len(nums)//2]

---------------------------------------------------
	Every number in the vector votes for itself, the majority number gets the most votes. Different number offsets the votes.
	
	主要元素说明这个元素出现的次数大于1/2次。
	简言之，相同的元素count加一，不同元素抵消count。count为0，说明这个元素前面已经被抵消。数量占优的元素必然至少count>=1

	public class Solution {
	    public int majorityElement(int[] num) {
	
	        int major=num[0], count = 1;
	        for(int i=1; i<num.length;i++){
	            if(count==0){
	                count++;
	                major=num[i];
	            }else if(major==num[i]){
	                count++;
	            }else count--;
	            
	        }
	        return major;
	    }
	}
        
