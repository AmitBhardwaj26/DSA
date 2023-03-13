
<h2><a href="https://leetcode.com/problems/symmetric-tree/">101. Symmetric Tree</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given the root of a binary tree, check whether it is a mirror of itself (i.e., symmetric around its center).
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  root = [1,2,2,3,4,4,3]
<strong>Output:</strong>  true
</pre>


Constraints:
<pre>
The number of nodes in the tree is in the range [1, 1000].
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

