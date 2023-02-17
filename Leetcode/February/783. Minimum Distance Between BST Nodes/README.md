
<h2><a href="https://leetcode.com/problems/minimum-distance-between-bst-nodes/description/"></a>783. Minimum Distance Between BST Nodes</h2>
<h3>Easy</h3>
<hr>
<div><p>
 Given the root of a Binary Search Tree (BST), return the minimum difference between the values of any two different nodes in the tree.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  root = [4,2,6,1,3]
<strong>Output:</strong>  1
</pre>


Constraints:
<pre>
The number of nodes in the tree is in the range [2, 100].
0 <= Node.val <= 105
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
        
class Solution {
public:
    vector<int> v;
    void solve(TreeNode *t)
    {
        if(t==NULL) return;
        solve(t->left);
        v.push_back(t->val);
        solve(t->right);
    }
   
    int minDiffInBST(TreeNode* root) {
        solve(root);
        int ans=INT_MAX;
        for(int i=1;i<v.size();i++)
        {
            ans=min(ans,v[i]-v[i-1]);
        }
        return ans;
    }
};
          
 </pre>

