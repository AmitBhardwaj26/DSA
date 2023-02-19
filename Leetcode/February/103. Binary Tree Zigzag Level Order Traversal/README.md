
<h2><a href="https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/description/">103. Binary Tree Zigzag Level Order Traversal</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given the root of a binary tree, return the zigzag level order traversal of its nodes' values. (i.e., from left to right, then right to left for the next level and alternate between).

 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   root = [3,9,20,null,null,15,7]
<strong>Output:</strong> [[3],[20,9],[15,7]]
</pre>
 

Constraints:
<pre>
The number of nodes in the tree is in the range [0, 2000].
-100 <= Node.val <= 100
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
class Solution {
public:
    vector<vector<int>> zigzagLevelOrder(TreeNode* root) {
        bool check=false;
        
        vector<vector<int>> v1; vector<int> v;
        TreeNode *t1=root ,*t=NULL;
        
        queue<TreeNode*> q1;
        if(t1) q1.push(t1);
        
        while(!q1.empty())
        {
            int n=q1.size();
            while(n-- ) {
                 t=q1.front();  q1.pop(); v.push_back(t->val);  cout<<t->val<<" ";
           
                           if(t->left)  q1.push(t->left);  
                             if(t->right) q1.push(t->right); 
                            }
            if(check) {reverse(v.begin(),v.end()); check=false;}
            else check=true;
            v1.push_back(v); v.clear();
        }
            return v1;
    }
};
          
 </pre>

