
<h2><a href="https://leetcode.com/problems/binary-tree-preorder-traversal/description/">144. Binary Tree Preorder Traversal</a></h2>
<h3>Easy</h3>
<hr>
<div><p>
Given the root of a binary tree, return the preorder traversal of its nodes' values.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   root = [1,null,2,3]
<strong>Output:</strong>[1,2,3]
</pre>

  

 

Constraints:
<pre>
The number of nodes in the tree is in the range [0, 100].
-100 <= Node.val <= 100
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
    class Solution {
      public:
          vector<int> preorderTraversal(TreeNode* root) {
              vector<int> v; TreeNode *t=root;
              stack<TreeNode*> st;
              while(t || !st.empty())
              {
                  if(t)
                  {
                      v.push_back(t->val);
                      st.push(t);
                      t=t->left;
                  }
                  else 
                  {
                      TreeNode *p=st.top(); st.pop();
                      t=p->right;

                  }

              }
              return v;
          }
      };
          
 </pre>

