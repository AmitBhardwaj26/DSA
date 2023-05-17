
<h2><a href="https://leetcode.com/problems/path-sum-ii/"> 113.Path Sum II</a></h2>
<h3>Medium</h3>
<hr>
<div><p>

Given the root of a binary tree and an integer target Sum, return all root-to-leaf paths where the sum of the node values in the path equals targetSum. Each path should be returned as a list of the node values, not node references.

A root-to-leaf path is a path starting from the root and ending at any leaf node. A leaf is a node with no children.
</p>

<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   root = [5,4,8,11,null,13,4,7,2,null,null,5,1], targetSum = 22
<strong>Output:</strong> [[5,4,11,2],[5,8,4,5]]
</pre>
<pre>
There are two paths whose sum equals targetSum:
5 + 4 + 11 + 2 = 22
5 + 8 + 4 + 5 = 22
</pre>
  
<p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong>  root = [1,2,3], targetSum = 5
<strong>Output:</strong> [ ]
</pre>  

Constraints:
<pre>
The number of nodes in the tree is in the range [0, 5000].
-1000 <= Node.val <= 1000
-1000 <= targetSum <= 1000

</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
class Solution {
    public:
            
     vector<vector<int>> v;
        void find(TreeNode *root, vector<int> v1,int t)
        {
                     
            if(!root)  {return; } 
            v1.push_back(root->val);
        if((t-root->val)==0 && !root->left && !root->right) 
           v.push_back(v1);   
           
        
        find( root->left,v1,t-root->val);
        find( root->right,v1,t-root->val);  
        }
    
        vector<vector<int>> pathSum(TreeNode* root, int t) 
        {
           
             vector<int> v1;
             find(root,v1,t);
             return v;
            
        }
};
          
 </pre>

