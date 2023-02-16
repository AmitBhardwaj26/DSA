
<h2><a href="https://leetcode.com/problems/sum-of-even-numbers-after-queries/">104. Maximum Depth of Binary Tree</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given the root of a binary tree, return its maximum depth.

A binary tree's maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  root = [3,9,20,null,null,15,7]
<strong>Output:</strong>  3
</pre>
<pre>
Explanation: 
  </pre>
  
Example 2:

Input: nums = [1], queries = [[4,0]]
Output: [0]
 

Constraints:
<pre>
The number of nodes in the tree is in the range [0, 104].
-100 <= Node.val <= 100
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

