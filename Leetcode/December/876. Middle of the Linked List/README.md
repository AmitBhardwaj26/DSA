
<h2><a href="https://leetcode.com/problems/sum-of-even-numbers-after-queries/">876. Middle of the Linked List</a></h2>
<h3>Easy</h3>
<hr>
<div><p>
Given the head of a singly linked list, return the middle node of the linked list.

If there are two middle nodes, return the second middle node.

</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  head = [1,2,3,4,5]
<strong>Output:</strong> [3,4,5]
</pre>
<pre>
The middle node of the list is node 3.
  </pre>


Constraints:
<pre>
1 <= nums.length <= 104
-104 <= nums[i] <= 104
1 <= queries.length <= 104
-104 <= vali <= 104
0 <= indexi < nums.length
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
        /*
1: simple length based l/2 then travesed
2: using fast and slow pointer
*/

class Solution {
public:
    ListNode* middleNode(ListNode* head) {
        ListNode* slow, *fast=head;
        while(fast!=NULL && fast->next!=NULL)
        {
            slow=slow->next;
            fast=fast->next->next;
        }
        return slow;
    }
};



// class Solution {
// public:
//     ListNode* middleNode(ListNode* head) {
//         int l=0;
//         ListNode *t=head;
//         while(t) {t=t->next; l++;}
//         l=l/2;
//         while(l--){ head=head->next; }
//         return head;
//     }
// };
          
 </pre>

