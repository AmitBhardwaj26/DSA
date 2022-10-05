
<h2><a href="https://leetcode.com/problems/sum-of-even-numbers-after-queries/">985. Sum of Even Numbers After Queries</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given the root of a binary tree and two integers val and depth, add a row of nodes with value val at the given depth depth.

Note that the root node is at depth 1.

The adding rule is:

Given the integer depth, for each not null tree node cur at the depth depth - 1, create two tree nodes with value val as cur's left subtree root and right subtree root.
cur's original left subtree should be the left subtree of the new left subtree root.
cur's original right subtree should be the right subtree of the new right subtree root.
If depth == 1 that means there is no depth depth - 1 at all, then create a tree node with value val as the new root of the whole original tree, and the original tree is the new root's left subtree.
 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  root = [4,2,6,3,1,5], val = 1, depth = 2
<strong>Output:</strong> [4,1,1,2,null,null,6,3,1,5]
</pre>

  
Example 2:

Input: root = [4,2,null,3,1], val = 1, depth = 3
Output: [4,2,null,1,1,3,null,null,1]
 

Constraints:
<pre>
The number of nodes in the tree is in the range [1, 104].
The depth of the tree is in the range [1, 104].
-100 <= Node.val <= 100
-105 <= val <= 105
1 <= depth <= the depth of tree + 1
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 class Solution {
public:
    TreeNode* addOneRow(TreeNode* root, int val, int d) {
        TreeNode *temp;
        if(d==1) 
        {
            temp=new TreeNode(val); temp->left=root; return temp;
        }

        queue<TreeNode*> q;
        q.push(root);
        while(!q.empty())
        {
            int x=q.size();
            if(d==2)
            {
              while(x--)
              {
                temp=q.front(); q.pop();
                TreeNode *leftt= temp->left,*rightt=temp->right ;
                TreeNode *newleft=new TreeNode(val); 
                TreeNode *newright=new TreeNode(val);
                  newleft->left=leftt; 
                 newright->right=rightt;
                 temp->left=newleft, temp->right=newright;
              }
               return root;
            }
            while(x--)
            {
                temp=q.front(); q.pop();
                if(temp->left) q.push(temp->left);
                if(temp->right) q.push(temp->right);
            }
           d--;
        }
        return root;
    }
};
 </pre>

