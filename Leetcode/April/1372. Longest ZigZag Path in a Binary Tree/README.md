
<h2><a href="https://leetcode.com/problems/longest-zigzag-path-in-a-binary-tree/">1372. Longest ZigZag Path in a Binary Tree</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
You are given the root of a binary tree.

A ZigZag path for a binary tree is defined as follow:

Choose any node in the binary tree and a direction (right or left).
If the current direction is right, move to the right child of the current node; otherwise, move to the left child.
Change the direction from right to left or from left to right.
Repeat the second and third steps until you can't move in the tree.
Zigzag length is defined as the number of nodes visited - 1. (A single node has a length of 0).

Return the longest ZigZag path contained in that tree.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   root = [1,null,1,1,1,null,null,1,1,null,1,null,null,null,1,null,1]
<strong>Output:</strong> [8,6,2,4]
</pre>
<pre>
Explanation: Longest ZigZag path in blue nodes (right -> left -> right).
  </pre>


Constraints:
<pre>
The number of nodes in the tree is in the range [1, 5 * 104].
1 <= Node.val <= 100
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
class Solution {
public:
    int ans=0;
    void solve(TreeNode* root, int dir,int count)
    {
        if(root==NULL) return ;
        ans=max(ans,count);
        if(dir==1) 
        {
            solve(root->left,1,1);
            solve(root->right,2,count+1);
        }
        else 
        {
          solve(root->left,1,count+1);
          solve(root->right,2,1);
        } 
        return ;
    }
    
    int longestZigZag(TreeNode* root) {
        solve(root->left,1,1);
        solve(root->right,2,1);
        return ans;
    }
};
 </pre>

