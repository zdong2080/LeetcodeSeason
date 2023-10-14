# [24. Swap Nodes in Pairs](https://leetcode.com/problems/swap-nodes-in-pairs/description/)

time: O(n)\
space: O(1) 

### Idea
Use three moving pointers and one stable pointer point to the start position \
[  1,    2,    3,  4,  5,  6] \
   ^     ^    ^  \
 last  curr  next \
using a loop to check curr != null \
each iteration doing the following stuff: \
1: point curr next pointer to last \
2: check if next == null \
2-a: if null, pointer last next to null to prevent circle \
2-b: if not null, check if next.next is null \
3-a: if null, we know next is last element \
point last next pointer to next and break \
3-b: if not null, point last next pointer to next.next \
and move last to next, curr to next.next \
and set next to curr next

### Java
``` java
class Solution {
    public ListNode swapPairs(ListNode head) {
        // length = 0
        // length = 1
        if(head == null) return null;
        if(head.next == null) return head;
        ListNode dummy = head.next;

        ListNode last, curr, next;
        last = head;
        curr = last.next;
        next = curr.next;
        while(curr != null) {
            curr.next = last;
            if(next == null) {
                last.next = null;
                break;
            }
            else {
                if(next.next == null) {
                    last.next = next;
                    break;
                }
                else {
                    last.next = next.next;
                    last = next;
                    curr = next.next;
                    next = curr.next;
                }
            }

        }
        
        return dummy;
    }
}
```

# [19. Remove Nth Node From End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/)

time: O(n) \
space: O(1) 

### Need redo
two pointer problem \
move fast n time, then move fast and slow together \
set pred point to head \
move along with slow \
when fast reach the end of the linked list, slow stop at n node from last node \
and point pred next pointer to slow next node

### Java
``` java
class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {
        if(head.next == null) return null; 

        int needToMove = n - 1;
        ListNode slow, fast;
        ListNode pred = new ListNode(0);
        pred.next = head;

        slow = head;
        fast = head;
        while(needToMove > 0) {
            fast = fast.next;
            needToMove--;
        }

        while(fast.next != null) {
            slow = slow.next;
            fast = fast.next;
            pred = pred.next;
        }

        pred.next = slow.next;

        if(slow == head && pred.next != head) return pred.next;

        return head;
    }
}
```


# [142. Linked List Cycle II](https://leetcode.com/problems/linked-list-cycle-ii/description/)

time: O(n) \
space: O(1)

### Idea
done this before

### Java
``` java
public class Solution {
    public ListNode detectCycle(ListNode head) {
        ListNode fast, slow;
        fast = head;
        slow = head;

        while(fast != null && fast.next != null && fast.next.next != null) {
            fast = fast.next.next;
            slow = slow.next;
            if(fast == slow) break;
        }

        fast = head;

        while(slow != null && slow.next != null && fast != null && fast.next != null) {
            fast = fast.next;
            slow = slow.next;
            if(fast == slow && fast.next == head && slow.next == head) return head;
            if(fast == slow && fast.next != null) return fast;
        }

        return null;
    }
}
```
