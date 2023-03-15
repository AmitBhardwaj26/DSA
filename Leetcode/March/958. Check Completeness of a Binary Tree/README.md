
<h2><a href="https://leetcode.com/problems/check-completeness-of-a-binary-tree/description/">958. Check Completeness of a Binary Tree</a></h2>
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
 /**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    bool isCompleteTree(TreeNode* root) {
        if (root == nullptr) {
            return true;
        }
        queue<TreeNode*> q;
        q.push(root);
      
        bool  nullNodeFound=0;
        while(!q.empty())
        {
                TreeNode* node=q.front(); q.pop();

                if (node == nullptr) {         nullNodeFound = true;  }
                else {    if (nullNodeFound)     return false;         
                
                q.push(node->left);
                q.push(node->right);
                }
        }       
       
        return 1;
    }
};
 </pre>

