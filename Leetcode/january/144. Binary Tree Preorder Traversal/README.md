
<h2><a href="https://leetcode.com/problems/binary-tree-preorder-traversal/description/">144. Binary Tree Preorder Traversal</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given the root of a binary tree, return the preorder traversal of its nodes' values.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   root = [1,null,2,3]
<strong>Output:</strong>[1,2,3]
</pre>

  

 

Constraints:
<pre>
The number of nodes in the tree is in the range [0, 100].
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

