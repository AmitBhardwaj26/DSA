
<h2><a href="https://leetcode.com/problems/two-sum-iv-input-is-a-bst/description/">653. Two Sum IV - Input is a BST</a></h2>
<h3>Easy</h3>
<hr>
<div><p>
  Given the root of a Binary Search Tree and a target number k, return true if there exist two elements in the BST such that their sum is equal to the given target.
 </p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>    root = [5,3,6,2,4,null,7], k = 9
<strong>Output:</strong>  true
</pre>



Constraints:
<pre>
The number of nodes in the tree is in the range [1, 104].
-104 <= Node.val <= 104
root is guaranteed to be a valid binary search tree.
-105 <= k <= 105
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
          class Solution {
public:
    vector<int> v;
    void Tree(TreeNode *t)
    {
        if(!t) return;
        v.push_back(t->val);
        Tree(t->left);
        Tree(t->right);
    }
    
    bool findTarget(TreeNode* root, int k) {
        TreeNode *t=root;
        Tree(root);
        sort(v.begin(),v.end());
        int i=0, j=v.size()-1;
        while(i<j)
        {
            if(v[i]+v[j]==k) { v.clear(); return true;}
            else if((v[i]+v[j])>k) j--;
            else i++;
        }
        return false;
    }
};
         
 </pre>
 

