
<h2><a href="https://leetcode.com/problems/leaf-similar-trees/description/">872. Leaf-Similar Trees</a></h2>
<h3></h3>
<hr>
<div><p>
Consider all the leaves of a binary tree, from left to right order, the values of those leaves form a leaf value sequence.
  For example, in the given tree above, the leaf value sequence is (6, 7, 4, 9, 8).

Two binary trees are considered leaf-similar if their leaf value sequence is the same.

Return true if and only if the two given trees with head nodes root1 and root2 are leaf-similar.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  root1 = [3,5,1,6,2,9,8,null,null,7,4], root2 = [3,5,1,6,7,4,2,null,null,null,null,null,null,9,8]
<strong>Output:</strong> true
</pre>

  


Constraints:
<pre>
The number of nodes in each tree will be in the range [1, 200].
Both of the given trees will have values in the range [0, 200].
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
    void leaf(TreeNode* root,vector<int> &v)
    {
        if(!root) return ;
        leaf(root->left,v);
        if(!root->left && !root->right) v.push_back(root->val);
        leaf(root->right,v);
        return ;
    }

    bool leafSimilar(TreeNode* root1, TreeNode* root2) {
        vector<int> v1,v2;
        leaf(root1,v1);
        leaf(root2,v2);
        int i=0,j=0;
        while(i<v1.size() && i<v2.size())
        {
            if(v1[i]!=v2[i]) return 0;
            i++;
        }
        while(i<v1.size())
        {
            return 0;
        }
        while(i<v2.size()) return 0;
        return 1;
    }
};
          
 </pre>

