# Leetcode 206: Reverse Linked List

🔗 [View Problem on LeetCode](https://leetcode.com/problems/reverse-linked-list/)

---

## Problem Statement

Given the head of a singly linked list, reverse the list and return the new head.


##  Approach: Iterative Method (Using Three Pointers)

We use three pointers:

- `prev` → stores the previous node (initially `null`)
- `curr` → current node (starts at head)
- `next` → temporarily stores `curr.next` so it's not lost

### 💡 Steps:

1. While `curr` is not null:
   - Save the next node: `next = curr.next`
   - Reverse the link: `curr.next = prev`
   - Move `prev` forward: `prev = curr`
   - Move `curr` forward: `curr = next`
2. When the loop ends, `prev` is the new head of the reversed list.

---

## Java Code (Iterative + Dry Run + Complexity)

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
    public ListNode reverseList(ListNode head) {
        ListNode prev = null;
        ListNode curr = head;

        while (curr != null) {
            ListNode next = curr.next;
            curr.next = prev;
            prev = curr;
            curr = next;
        }

        return prev;
    }
}

/*
⏱️ Time Complexity: O(n)
We visit each node once.

📦 Space Complexity: O(1)
Only pointers used, no extra memory.

🧪 Example Dry Run:

Input: 1 -> 2 -> 3 -> 4 -> 5 -> null

Initial:
prev = null
curr = 1

Step 1:
next = 2
curr.next = null (reverse link)
prev = 1
curr = 2

Step 2:
next = 3
curr.next = 1
prev = 2
curr = 3

Step 3:
next = 4
curr.next = 2
prev = 3
curr = 4

Step 4:
next = 5
curr.next = 3
prev = 4
curr = 5

Step 5:
next = null
curr.next = 4
prev = 5
curr = null

Reversed List: 5 -> 4 -> 3 -> 2 -> 1 -> null
*/

