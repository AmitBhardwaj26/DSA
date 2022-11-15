
<h2><a href="https://leetcode.com/problems/count-complete-tree-nodes/">222. Count Complete Tree Nodes</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given the root of a complete binary tree, return the number of the nodes in the tree.

According to Wikipedia, every level, except possibly the last, is completely filled in a complete binary tree, and all nodes in the last level are as far left as possible. It can have between 1 and 2h nodes inclusive at the last level h.

Design an algorithm that runs in less than O(n) time complexity.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   root = [1,2,3,4,5,6]
<strong>Output:</strong>6
</pre>

  
Example 2:

Input: root = []
Output: 0
 

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
            int countNodes(TreeNode* root) {
                if(!root) return 0;
                return 1+countNodes(root->left)+ countNodes(root->right);
            }
        };
          
 </pre>

