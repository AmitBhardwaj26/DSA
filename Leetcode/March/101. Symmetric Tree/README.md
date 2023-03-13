
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
    bool check(TreeNode* t1, TreeNode* t2)
    {
        if(!t1 && !t2) return 1;
         if(!t1 || !t2) return 0;
        if(t1->val != t2->val) return 0; 
        return check(t1->right,t2->left)&&check(t1->left,t2->right);
    }
    
    bool isSymmetric(TreeNode* root) {
        return check(root->left,root->right);
    }
};
 </pre>

