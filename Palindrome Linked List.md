# Palindrome Linked List
**Solution:** Use the fast and slow pointer to find the middle of the list, reverse the first half of the list and compare it to the rest half.

**Time Complexity:** O(n)

**Space Complexity:** O(1)


```java
    public boolean isPalindrome(ListNode head) {
        if(head == null || head.next == null) return true;
        
        ListNode temp;
        ListNode prev;
        ListNode fast;
        ListNode slow;
        
        slow = head;
        fast = head.next;
        prev = null;
        temp = null;
        
        while(fast.next!=null && fast.next.next!=null){
            //build the reverse list
            prev = temp;
            temp = slow;
            slow = slow.next;
            temp.next = prev;
            //move the slow and fast nodes
            fast = fast.next.next;
        }
        //move the slow node to the start of the rest part of the list
        if(fast.next == null){
            //complete the reverse list
            prev = temp;
            temp = slow;
            slow = slow.next;
            temp.next = prev;
        }
        else if (fast.next.next == null){
            prev = temp;
            temp = slow;
            slow = slow.next;
            temp.next = prev;
            slow = slow.next;
        }
        while(slow!=null && temp!=null){
            if(slow.val!=temp.val) return false;
            slow = slow.next;
            temp = temp.next;
        }
        return true;
    }
```