### 13	Roman to Integer  

	class Solution:
    def romanToInt(self, s):
        """
        :type s: str
        :rtype: int
        """
        def getNum( key ):
            diction = {
                'I': 1,
                'V': 5,
                'X': 10,
                'L': 50,
                'C': 100,
                'D': 500,
                'M': 1000

            }
            return diction[key]
        
        sum = getNum(s[0])
        currNum = 0
        prevNum = sum
        # print(sum)

        for i in range(1, len(s)):
            currNum = getNum(s[i])
            # print(currNum)
            if currNum <= prevNum:
                sum += currNum
            else:
                sum = sum + currNum - 2*prevNum
            prevNum = currNum

        return sum
