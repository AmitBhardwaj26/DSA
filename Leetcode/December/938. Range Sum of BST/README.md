
<h2><a href="https://leetcode.com/problems/range-sum-of-bst/description/">938. Range Sum of BST</a></h2>
<h3>Easy</h3>
<hr>
<div><p>
Given the root node of a binary search tree and two integers low and high, return the sum of values of all nodes with a value in the inclusive range [low, high].

</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   root = [10,5,15,3,7,null,18], low = 7, high = 15
<strong>Output:</strong>  32
</pre>
<pre>
Nodes 7, 10, and 15 are in the range [7, 15]. 7 + 10 + 15 = 32.
  </pre>
  
<pre>  
Input: root = [10,5,15,3,7,13,18,1,null,6], low = 6, high = 10
Output: 23
Explanation: Nodes 6, 7, and 10 are in the range [6, 10]. 6 + 7 + 10 = 23.
 </pre>

Constraints:
<pre>
The number of nodes in the tree is in the range [1, 2 * 104].
1 <= Node.val <= 105
1 <= low <= high <= 105
All Node.val are unique.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 class Solution {
public:
    vector<int> v;
    void preorder(TreeNode *t)
    {
        if(!t) return;
        v.push_back(t->val);
        preorder(t->left);
        preorder(t->right);
    }
    
    int rangeSumBST(TreeNode* root, int low, int high) {
        preorder(root); int ans=0;
    for(int i=0;i<v.size();i++)
    {
        if(v[i]>=low && v[i]<=high) ans+=v[i];
    }
        return ans;
    }
};
          
 </pre>

