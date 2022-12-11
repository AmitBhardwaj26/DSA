
<h2><a href="https://leetcode.com/problems/binary-tree-maximum-path-sum/description/">124. Binary Tree Maximum Path Sum</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
A path in a binary tree is a sequence of nodes where each pair of adjacent nodes in the sequence has an edge connecting them. A node can only appear in the sequence at most once. Note that the path does not need to pass through the root.

The path sum of a path is the sum of the node's values in the path.

Given the root of a binary tree, return the maximum path sum of any non-empty path.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  root = [1,2,3]
<strong>Output:</strong> 6
</pre>
<pre>
Explanation: The optimal path is 2 -> 1 -> 3 with a path sum of 2 + 1 + 3 = 6.
  </pre>
  

 

Constraints:
<pre>
The number of nodes in the tree is in the range [1, 3 * 104].
-1000 <= Node.val <= 1000
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
    int ans=INT_MIN;
    int Max(TreeNode* root)
    {
        if(!root) return 0;
        int left =max(0, Max(root->left));
        int right=max(0, Max(root->right));
        ans=max(ans,root->val+left+right );
        return root->val + max(left,right);
    }
    int maxPathSum(TreeNode* root) {
       
        Max(root);
        return ans;
    }
};
          
 </pre>

