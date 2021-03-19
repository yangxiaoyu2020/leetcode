[面试了蚂蚁来做道题。平复一下心情。](复一下心情。)

### 解题思路
本质上可以通过画图来理清思路
### 代码
#### 1第一种解法
- 想办法让他退化成 普通的反转链表

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode reverseBetween(ListNode head, int left, int right) {
        ListNode pre = new ListNode(0);
        ListNode leftNode = null;
        ListNode rightNode = null;
        pre.next = head;
        ListNode res = pre;
        for(int i = 0; i < left - 1; i++) {
            pre = pre.next;
        }
        rightNode = pre.next;
        for(int i = 0; i < right - left; i++) {
            rightNode = rightNode.next;
        }
        leftNode = pre.next;
        ListNode cur = rightNode.next;
        pre.next = null;
        rightNode.next = null;

        reverse(leftNode);
        pre.next = rightNode;
        leftNode.next = cur;
        return res.next;


    }

    private ListNode reverse(ListNode head) {
        ListNode pre = null;
        ListNode cur = head;
        while (cur!=null) {
            ListNode tmp = cur.next;
            cur.next = pre;
            pre = cur;
            cur = tmp;
        }
        return pre;
    }

### 第二种就是先拿到
1 2 3 4 5
_ ^ _ _ _

然后
2 3 4 5

2->3->4->5 => 4<-2<-3 4->5 =>  2<-3<-4 5 =>  5<-2<-3<-4
利用 tmp 不断移动来反转
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode reverseBetween(ListNode head, int left, int right) {
        ListNode res = new ListNode(0);
        res.next = head;
        ListNode pre = res;
        for (int i = 0; i < left - 1; i++) {
            pre = pre.next;
        }
        ListNode cur = pre.next;
        ListNode tmp = null;
        for (int i = 0; i < right - left; i++) {
            tmp = cur.next;
            cur.next = tmp.next;
            tmp.next = pre.next;
            pre.next = tmp;
        }
        return res.next;
    }
}
```
