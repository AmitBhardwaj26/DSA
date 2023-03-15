
<h2><a href="https://leetcode.com/problems/sum-of-even-numbers-after-queries/">958. Check Completeness of a Binary Tree</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given the root of a binary tree, determine if it is a complete binary tree.

In a complete binary tree, every level, except possibly the last, is completely filled, and all nodes in the last level are as far left as possible. It can have between 1 and 2h nodes inclusive at the last level h.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> root = [1,2,3,4,5,6]
<strong>Output:</strong> true
</pre>
<pre>
Explanation:  Every level before the last is full (ie. levels with node-values {1} and {2, 3}), and all nodes in the last level ({4, 5, 6}) are as far left as possible.
  </pre>
 

Constraints:
<pre>
The number of nodes in the tree is in the range [1, 100].
1 <= Node.val <= 1000
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

