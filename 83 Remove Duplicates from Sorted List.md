### 83	Remove Duplicates from Sorted List

	# Definition for singly-linked list.
	# class ListNode(object):
	#     def __init__(self, x):
	#         self.val = x
	#         self.next = None
	
	class Solution(object):
	    def deleteDuplicates(self, head):
	        """
	        :type head: ListNode
	        :rtype: ListNode
	        """
			#curr用来改变head的指向
	        curr = head
	        while curr:
				#curr.next.next = None刚好可以退出内层循环
				#有下一个节点且下一个节点等于当前节点才执行内循环
	            while curr.next and curr.next.val == curr.val:
	                curr.next = curr.next.next
	            curr = curr.next
	        return head