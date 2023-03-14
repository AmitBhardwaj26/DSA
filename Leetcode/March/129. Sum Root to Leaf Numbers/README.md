
<h2><a href="https://leetcode.com/problems/sum-root-to-leaf-numbers/description/">129. Sum Root to Leaf Numbers</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
You are given the root of a binary tree containing digits from 0 to 9 only.

Each root-to-leaf path in the tree represents a number.

For example, the root-to-leaf path 1 -> 2 -> 3 represents the number 123.
Return the total sum of all root-to-leaf numbers. Test cases are generated so that the answer will fit in a 32-bit integer.

A leaf node is a node with no children.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   root = [1,2,3]
<strong>Output:</strong> 25
</pre>
<pre>
Explanation: The root-to-leaf path 1->2 represents the number 12.
The root-to-leaf path 1->3 represents the number 13.
Therefore, sum = 12 + 13 = 25.
  </pre>
  


Constraints:
<pre>
1 <= nums.length <= 104
-104 <= nums[i] <= 104
1 <= queries.length <= 104
-104 <= vali <= 104
0 <= indexi < nums.length
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
class Solution {
public:
    int ans=0;
    void sol(TreeNode* root,string s)
    {
        if(!root) return;
        s+=to_string(root->val);
        if(!root->left && !root->right) 
        {
            ans+=stoi(s); return; 
        }
        sol(root->left,s);
        sol(root->right,s);  
    }
    int sumNumbers(TreeNode* root) {
        sol(root,"");
        return ans;
    }
};
 </pre>

