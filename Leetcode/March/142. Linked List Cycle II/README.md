
<h2><a href="https://leetcode.com/problems/linked-list-cycle-ii/description/">142. Linked List Cycle II</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
 Given the head of a linked list, return the node where the cycle begins. If there is no cycle, return null.

There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the next pointer. Internally, pos is used to denote the index of the node that tail's next pointer is connected to (0-indexed). It is -1 if there is no cycle. Note that pos is not passed as a parameter.

Do not modify the linked list.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   head = [3,2,0,-4], pos = 1
<strong>Output:</strong> tail connects to node index 1
</pre>
<pre>
Explanation: There is a cycle in the linked list, where tail connects to the second node.tail connects to node index 1
  </pre>
  


Constraints:
<pre>
The number of the nodes in the list is in the range [0, 104].
-105 <= Node.val <= 105
pos is -1 or a valid index in the linked-list.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 /**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode *detectCycle(ListNode *head) {
        ListNode *slow=head,*fast=head;
        do
        {
            if(slow) slow=slow->next;
            if(fast) fast=fast->next;
            if(fast) fast=fast->next;
            else return 0;
        }
        while(slow && fast && fast!=slow);
        if(fast) fast=head;
        
        do
        {
            if(fast==slow) return slow;
        
            if(slow) slow=slow->next;
            if(fast) fast=fast->next;
            if(fast==slow) return slow;
        
        }
        while(slow && fast && fast!=slow);
        
        return 0;
    }
};
 </pre>

