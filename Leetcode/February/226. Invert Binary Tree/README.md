
<h2><a href="https://leetcode.com/problems/sum-of-even-numbers-after-queries/">226. Invert Binary Tree</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given the root of a binary tree, invert the tree, and return its root.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   root = [4,2,7,1,3,6,9]
<strong>Output:</strong> [4,7,2,9,6,3,1]
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
    TreeNode* invertTree(TreeNode* root) {
        if(!root) return NULL;
         TreeNode *temp=root->left; 
         root->left=root->right;
         root->right =temp;
        TreeNode *l=invertTree(root->left);
        TreeNode *r=invertTree(root->right);
      
        return root;
    }
};
          
 </pre>

