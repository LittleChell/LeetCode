### 14	Longest Common Prefix  

	prefixArr = [];
        lenStr = len(strs)
        if lenStr == 0: return ""
        shortStr = strs[0]
        shortLen = len( shortStr )
        resultStr = shortStr[:]
        minerLen = 0
        for i in range(1, len(strs)):
            currStr = strs[i]
            currLen = len(currStr)
            if shortLen < currLen:
                minerLen = shortLen 
            else:
                minerLen = currLen
                shortStr = shortStr[:currLen]
                shortLen = currLen
            if minerLen == 0:   return ""
            print(minerLen, shortLen)
            for j in range(minerLen):
                if currStr[j] != shortStr[j]:   
                    shortStr = shortStr[:j]
                    shortLen = len( shortStr )
                    break

        return shortStr