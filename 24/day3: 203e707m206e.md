# [203. Remove Linked List Elements](https://leetcode.com/problems/remove-linked-list-elements/description/)

time: O(n)\
space: O(1) 

### Idea
keep a pointer and iterate the whole list

### Java
``` java
class Solution {
    public ListNode removeElements(ListNode head, int val) {
        ListNode dummy = new ListNode(0);
        ListNode p = dummy;
        while(head != null) {
            if(head.val != val) {
                p.next = head;
                p = p.next;
            }
            head = head.next;
        }
        p.next = null;
        return dummy.next;
    }
}

```

# [707. Design Linked List](https://leetcode.com/problems/design-linked-list/description/)

time: O(n) \
space: O(n) 

### Need redo
at first seeing this question, all focus is on the constructor and getIndex function \
meanwhile the variable inside the class is int val and MyLinkedList next \
which track my thought on ListNode logic \
The crucial point is to separate two classes in this question

### Java
``` java
public class ListNode {
    int val;
    ListNode next;
    ListNode(int x) { val = x; }
}

class MyLinkedList {
    int size;
    ListNode head;

    public MyLinkedList() {
        size = 0;
        head = new ListNode(0);
    }
    
    public int get(int index) {
        if (index < 0 || index >= size) return -1;

        ListNode curr = head;
        for(int i = 0; i < index + 1; ++i) curr = curr.next;
        return curr.val;
    }
    
    public void addAtHead(int val) {
        addAtIndex(0, val);
    }
    
    public void addAtTail(int val) {
        addAtIndex(size, val);
    }
    
    public void addAtIndex(int index, int val) {
        if (index > size) return;
        if (index < 0) index = 0;
        ++size;

        ListNode pred = head;
        for(int i = 0; i < index; ++i) pred = pred.next;

        ListNode toAdd = new ListNode(val);
        toAdd.next = pred.next;
        pred.next = toAdd;
    }
    
    public void deleteAtIndex(int index) {
        if (index < 0 || index >= size) return;

        size--;

        ListNode pred = head;
        for(int i = 0; i < index; ++i) pred = pred.next;

        pred.next = pred.next.next;
    }
}
```


# [206. Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/description/)

time: O(n) \
space: O(1)

### Idea
Record the current node, next node, pred node \
First keep the pointer of next node, then point the current node's next node to pred node \
Set pred node to current node, then move current pointer to next node

### Java
``` java
class Solution {
    public ListNode reverseList(ListNode head) {
        
        ListNode next;
        ListNode pred = null;

        while(head != null) {
            next = head.next;
            head.next = pred;
            pred = head;
            head = next;
        }

        return pred;
    }
}
```
