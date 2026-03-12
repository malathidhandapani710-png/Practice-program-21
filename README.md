class Solution:
    def isPalindrome(self, head):
        if not head or not head.next:
            return True
            
        # Step 1: Find the middle using slow and fast pointers
        slow = head
        fast = head
        while fast.next and fast.next.next:
            slow = slow.next
            fast = fast.next.next
            
        # Step 2: Reverse the second half of the list
        second_half_head = self.reverseList(slow.next)
        
        # Step 3: Compare the halves
        first_half_ptr = head
        second_half_ptr = second_half_head
        
        result = True
        while second_half_ptr:
            if first_half_ptr.data != second_half_ptr.data:
                result = False
                break
            first_half_ptr = first_half_ptr.next
            second_half_ptr = second_half_ptr.next
            
        return result

    def reverseList(self, head):
        prev = None
        curr = head
        while curr:
            next_node = curr.next
            curr.next = prev
            prev = curr
            curr = next_node
        return prev
