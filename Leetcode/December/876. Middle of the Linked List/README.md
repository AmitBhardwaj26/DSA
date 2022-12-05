
<h2><a href="https://leetcode.com/problems/sum-of-even-numbers-after-queries/">876. Middle of the Linked List</a></h2>
<h3>Medium</h3>
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
  
Example 2:

Input: nums = [1], queries = [[4,0]]
Output: [0]
 

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

