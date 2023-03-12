
<h2><a href="https://leetcode.com/problems/merge-k-sorted-lists/description/">23. Merge k Sorted Lists</a></h2>
<h3>Hard</h3>
<hr>
<div><p>
You are given an array of k linked-lists lists, each linked-list is sorted in ascending order.

Merge all the linked-lists into one sorted linked-list and return it.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   lists = [[1,4,5],[1,3,4],[2,6]]
<strong>Output:</strong> [1,1,2,3,4,4,5,6]
</pre>
<pre>
Explanation: The linked-lists are:
[
  1->4->5,
  1->3->4,
  2->6
]
merging them into one sorted list:
1->1->2->3->4->4->5->6
  </pre>


Constraints:
<pre>
k == lists.length
0 <= k <= 104
0 <= lists[i].length <= 500
-104 <= lists[i][j] <= 104
lists[i] is sorted in ascending order.
The sum of lists[i].length will not exceed 104.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
class Solution {
public:

    void insert(ListNode *head , ListNode *temp )
    {
        cout<<temp->val<<" ";
          ListNode *t=head,*p=NULL;
        if(!head || head->val>temp->val) {temp->next=head; head=temp;}
        else
        {
            while(t && t->val<=temp->val)
            {
              p=t;   t=t->next;
            }
            
           if(p) p->next=temp; temp->next=t;
        }
    }
    
    ListNode* mergeKLists(vector<ListNode*>& lists) {
        ListNode *head=NULL;
        
        for(int  i=0;i<lists.size();i++)
        {
            ListNode *t=lists[i],*p=NULL;
            while(t)
            {
                p=t->next;
                if(head && head->val>=t->val) {t->next=head; head=t;}
                else if(head==NULL) {head=t; t->next=NULL; cout<<head->val<<" ";} 
                else insert(head,t);
                
                t=p;
            }
        }
        return head;
    }
};
 </pre>

