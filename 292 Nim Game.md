### 292		Nim Game

	“使对方是4的倍数就能赢”
	class Solution(object):
    def canWinNim(self, n):
        """
        :type n: int
        :rtype: bool
        """
        return n%4 != 0