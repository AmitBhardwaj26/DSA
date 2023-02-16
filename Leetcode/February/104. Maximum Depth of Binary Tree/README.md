
<h2><a href="https://leetcode.com/problems/maximum-depth-of-binary-tree/description/">104. Maximum Depth of Binary Tree</a></h2>
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
    int maxDepth(TreeNode* root) {
        if(root==NULL){
            return 0;
        }
         return (1 + max(maxDepth(root->left),maxDepth(root->right)));
    }
};

// class Solution {
// public:
//     int maxDepth(TreeNode* root) {
        
//        if(root==NULL) return 0;
        
//         int l=maxDepth(root->left);
//         int r=maxDepth(root->right);
//         return l>=r?l+1:r+1;
        
//     }
// };
          
 </pre>

