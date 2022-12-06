
<h2><a href="https://leetcode.com/problems/odd-even-linked-list/description/">328. Odd Even Linked List</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given the head of a singly linked list, group all the nodes with odd indices together followed by the nodes with even indices, and return the reordered list.

The first node is considered odd, and the second node is even, and so on.

Note that the relative order inside both the even and odd groups should remain as it was in the input.

You must solve the problem in O(1) extra space complexity and O(n) time complexity.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   head = [1,2,3,4,5]
<strong>Output:</strong> [1,3,5,2,4]
</pre>
<pre>
Explanation: At the beginning, the array is [1,2,3,4].
After adding 1 to nums[0], the array is [2,2,3,4], and the sum of even values is 2 + 2 + 4 = 8.
After adding -3 to nums[1], the array is [2,-1,3,4], and the sum of even values is 2 + 4 = 6.
After adding -4 to nums[0], the array is [-2,-1,3,4], and the sum of even values is -2 + 4 = 2.
After adding 2 to nums[3], the array is [-2,-1,3,6], and the sum of even values is -2 + 6 = 4.
  </pre>


Constraints:
<pre>
The number of nodes in the linked list is in the range [0, 104].
-106 <= Node.val <= 106
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
        class Solution {
public:
    ListNode* oddEvenList(ListNode* head) {
        ListNode *odd=NULL, *o=NULL,*even=NULL, *e=NULL, *t=head;
        bool check=true;
        while(t)
        {
            if(check) 
            {
                if(!odd) { odd=t; o=t;}
                else { o->next=t; o=t;}
                check=false;
            }
            else 
            {
               if(!even) { even=t; e=t;}
                else { e->next=t;e=t;}
                check=true;                
            }
            t=t->next;
        }
       if(o) o->next=even;
       if(e) e->next=NULL;
        return head;
        
    }
};
          
 </pre>

