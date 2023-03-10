
<h2><a href="https://leetcode.com/problems/linked-list-random-node/description/">985. Sum of Even Numbers After Queries</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given a singly linked list, return a random node's value from the linked list. Each node must have the same probability of being chosen.

Implement the Solution class:

Solution(ListNode head) Initializes the object with the head of the singly-linked list head.
int getRandom() Chooses a node randomly from the list and returns its value. All the nodes of the list should be equally likely to be chosen.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> ["Solution", "getRandom", "getRandom", "getRandom", "getRandom", "getRandom"]
[[[1, 2, 3]], [], [], [], [], []]
<strong>Output:</strong> [null, 1, 3, 2, 2, 3]
</pre>
<pre>
Explanation:Solution solution = new Solution([1, 2, 3]);
solution.getRandom(); // return 1
solution.getRandom(); // return 3
solution.getRandom(); // return 2
solution.getRandom(); // return 2
solution.getRandom(); // return 3
// getRandom() should return either 1, 2, or 3 randomly. Each element should have equal probability of returning.
  </pre>


Constraints:
<pre>
The number of nodes in the linked list will be in the range [1, 104].
-104 <= Node.val <= 104
At most 104 calls will be made to getRandom.
 
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>

class Solution {
public:
     ListNode *headn=NULL;
    int l=0;
    Solution(ListNode* head) {
        headn=head;
        while(head)
        {
            l++;
            head=head->next;
        }
    }
    
    int getRandom() {
        ListNode *h=headn;
        //randomise();
        int z=rand()%l;
        while(z--)
        {
            h=h->next;
        }
        return h->val;
    }
};

 </pre>

