
<h2><a href="https://leetcode.com/problems/minimum-distance-between-bst-nodes/description/"></a>783. Minimum Distance Between BST Nodes</h2>
<h3>Medium</h3>
<hr>
<div><p>
 Given the root of a Binary Search Tree (BST), return the minimum difference between the values of any two different nodes in the tree.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  root = [4,2,6,1,3]
<strong>Output:</strong>  1
</pre>
<pre>
Explanation: At the beginning, the array is [1,2,3,4].
After adding 1 to nums[0], the array is [2,2,3,4], and the sum of even values is 2 + 2 + 4 = 8.
After adding -3 to nums[1], the array is [2,-1,3,4], and the sum of even values is 2 + 4 = 6.
After adding -4 to nums[0], the array is [-2,-1,3,4], and the sum of even values is -2 + 4 = 2.
After adding 2 to nums[3], the array is [-2,-1,3,6], and the sum of even values is -2 + 6 = 4.
  </pre>
  
Example 2:

Input: nums = [1], queries = [[4,0]]
Output: [0]
 

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

