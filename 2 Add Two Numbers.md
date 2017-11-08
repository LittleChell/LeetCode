### 2	Add Two Numbers

	链表指向的时候应该使用两个变量，一个变量保存整个链表，一个变量用来改变链表指向

	# Definition for singly-linked list.
	# class ListNode(object):
	#     def __init__(self, x):
	#         self.val = x
	#         self.next = None
	
	class Solution(object):
	    def addTwoNumbers(self, l1, l2):
	        """
	        :type l1: ListNode
	        :type l2: ListNode
	        :rtype: ListNode
	        """
	        int1, int2 = l1.val, l2.val
	        carry1, carry2 = 0, 0
	        while l1 and l1.next:
	            carry1 += 1
	            l1 = l1.next
	            int1 += l1.val*10**carry1
	        while l2 and l2.next:
	            carry2 += 1
	            l2 = l2.next
	            int2 += l2.val*10**carry2
	        count = int1 + int2
	        count = str(count)[::-1]
	        head = l = ListNode(count[0])
	        for x in count[1:]:
	            l3 = ListNode(x)
	            head.next = l3
	            head = head.next
	        return l