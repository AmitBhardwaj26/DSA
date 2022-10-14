
<h2><a href="https://leetcode.com/problems/delete-the-middle-node-of-a-linked-list/description/">2095. Delete the Middle Node of a Linked List</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
 You are given the head of a linked list. Delete the middle node, and return the head of the modified linked list.

The middle node of a linked list of size n is the ⌊n / 2⌋th node from the start using 0-based indexing, where ⌊x⌋ denotes the largest integer less than or equal to x.

For n = 1, 2, 3, 4, and 5, the middle nodes are 0, 1, 1, 2, and 2, respectively.
 </p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   head = [1,3,4,7,1,2,6]
<strong>Output:</strong> [1,3,4,1,2,6]
</pre>
<pre>
The above figure represents the given linked list. The indices of the nodes are written below.
Since n = 7, node 3 with value 7 is the middle node, which is marked in red.
We return the new list after removing this node. 
  </pre>
  
Example 2:

Input: nums = [1], queries = [[4,0]]
Output: [0]
 

Constraints:
<pre>
The number of nodes in the list is in the range [1, 105].
1 <= Node.val <= 105
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
          class Solution {
          public:
              vector<int> sumEvenAfterQueries(vector<int>& nums, vector<vector<int>>& q) {
                  int ans=0;
                  for(int i=0;i<nums.size();i++)
                  {
                      if(nums[i]%2==0) ans+=nums[i];
                  }
                  vector<int> v;
                  for(int i=0;i<q.size();i++)
                  {
                      int val=q[i][0],ind=q[i][1];
                      if(nums[ind]%2==0) ans-=nums[ind];
                      nums[ind]+=val;
                      if(nums[ind]%2==0) ans+=nums[ind];
                      v.push_back(ans);
                  }
                  return v;
              }
          };
          
 </pre>

