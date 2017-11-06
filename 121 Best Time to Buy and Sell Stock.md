### 121	Best Time to Buy and Sell Stock

	class Solution(object):
    def maxProfit(self, prices):
        """
        :type prices: List[int]
        :rtype: int
        """
        if not prices:  return 0
        (l, lVal) = (r, rVal) = ( 0, prices[0] )
        mSum = rVal - lVal
        for i in range(1, len(prices)):
        	if prices[i] < lVal:
        		(l, lVal) = (r, rVal) = (i, prices[i])
        	elif prices[i] > rVal and prices[i] - lVal > mSum:
        		mSum = prices[i] - lVal
        		(r, rVal) = (i, prices[i])
        return mSum