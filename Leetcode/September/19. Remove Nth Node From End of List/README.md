
<h2><a href="https://leetcode.com/problems/remove-nth-node-from-end-of-list/">19. Remove Nth Node From End of List</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given the head of a linked list, remove the nth node from the end of the list and return its head.

 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   head = [1,2,3,4,5], n = 2
<strong>Output:</strong> [1,2,3,5]
</pre>
  


Constraints:
<pre>
The number of nodes in the list is sz.
1 <= sz <= 30
0 <= Node.val <= 100
1 <= n <= sz
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
          class Solution {
public:
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        
        ListNode* t=head; int l=0;
    
        while(t) { l++;t=t->next;} 
        if(l==1 && n==1) return NULL;
        else if(l==n) return head->next;
        t=head; l=l-n-1; 
        while(l--) {t=t->next;} t->next=t->next->next;
        return head;
    }
};
 </pre>

