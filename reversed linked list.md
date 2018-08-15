# reversed linked list
**Solution:** The main problem I met is the corner cases that you should check the head first and then check the head.next.

**Time Complexity:** O(n)

**Space Complexity:** O(n)


```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public ListNode reverseList(ListNode head) {
        if(null == head){
            return head;
        }
        if(null == head.next){
            return head;
        }
        ListNode output = new ListNode(head.val);
        while(head.next != null) {
            head = head.next;
            ListNode tmp = new ListNode(head.val);
            tmp.next = output;
            output = tmp;
        }
        return output;
    }
}
```