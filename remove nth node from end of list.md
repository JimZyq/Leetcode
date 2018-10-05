# remove nth node from end of list
**Solution:** use the fast and slow node to pass the whole list, find the node and remove it. 

**Time Complexity:** O(n)

**Space Complexity:** O(n)


```java
    public ListNode removeNthFromEnd(ListNode head, int n) {
        if(n == 0) return head;
        ListNode prev = new ListNode(0);
        prev.next = head;
        ListNode temp;
        ListNode slow;
        ListNode fast;
        temp = prev;
        slow = head;
        fast = head;
        for(int i=0;i<n-1;i++){
            fast = fast.next;
        }
        while(fast.next != null){
            temp = slow;
            //System.out.println(temp.val);
            slow = slow.next;
            fast = fast.next;
        }
        temp.next = slow.next;
        return prev.next;
    }
```