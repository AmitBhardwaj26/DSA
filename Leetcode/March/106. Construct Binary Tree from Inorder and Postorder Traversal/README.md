
<h2><a href="https://leetcode.com/problems/construct-binary-tree-from-inorder-and-postorder-traversal/description/">106. Construct Binary Tree from Inorder and Postorder Traversal</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given two integer arrays inorder and postorder where inorder is the inorder traversal of a binary tree and postorder is the postorder traversal of the same tree, construct and return the binary tree.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   inorder = [9,3,15,20,7], postorder = [9,15,7,20,3]
<strong>Output:</strong> [3,9,20,null,null,15,7]
</pre>
<pre>
Explanation: At the beginning, the array is [1,2,3,4].
After adding 1 to nums[0], the array is [2,2,3,4], and the sum of even values is 2 + 2 + 4 = 8.
After adding -3 to nums[1], the array is [2,-1,3,4], and the sum of even values is 2 + 4 = 6.
After adding -4 to nums[0], the array is [-2,-1,3,4], and the sum of even values is -2 + 4 = 2.
After adding 2 to nums[3], the array is [-2,-1,3,6], and the sum of even values is -2 + 6 = 4.
  </pre>
  

Constraints:
<pre>
1 <= inorder.length <= 3000
postorder.length == inorder.length
-3000 <= inorder[i], postorder[i] <= 3000
inorder and postorder consist of unique values.
Each value of postorder also appears in inorder.
inorder is guaranteed to be the inorder traversal of the tree.
postorder is guaranteed to be the postorder traversal of the tree.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
class Solution {
public:
    TreeNode* buildTree(vector<int>& ino, vector<int>& post) {
    int i1 = post.size()-1;
        return solve(i1,ino,post,0,ino.size()-1);
    }
    TreeNode* solve(int &i,vector<int> &in,vector<int> &post,int l,int r){
        if(l>r)return NULL;
        int x = r;
        while(post[i] != in[x]){
            x--;
        }
        i--;
        TreeNode* root = new TreeNode(in[x]);
        root->right = solve(i,in,post,x+1,r);
        root->left = solve(i,in,post,l,x-1);
        return root;
    }
};
 </pre>

