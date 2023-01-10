
<h2><a href="https://leetcode.com/problems/same-tree/description/">100. Same Tree</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given the roots of two binary trees p and q, write a function to check if they are the same or not.

Two binary trees are considered the same if they are structurally identical, and the nodes have the same value.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  p = [1,2,3], q = [1,2,3]
<strong>Output:</strong> true
</pre>


 

Constraints:
<pre>
The number of nodes in both trees is in the range [0, 100].
-104 <= Node.val <= 104
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
          class Solution {
public:
    bool isSameTree(TreeNode* p, TreeNode* q) {
        if(!p && !q) return true;
        if((!p && q)||(p && !q)) return false;
        if(p->val!=q->val) return false;
            bool a= isSameTree(p->left,q->left);
            bool b= isSameTree(p->right,q->right);
        
        return a && b;
    }
};
 </pre>

