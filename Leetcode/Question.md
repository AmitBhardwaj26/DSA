
<h2><a href="https://leetcode.com/problems/binary-tree-pruning/">814. Binary Tree Pruning</a></h2>
<h3>Easy</h3>
<hr>
<div><p>Given the root of a binary tree, return the same tree where every subtree (of the given tree) not containing a 1 has been removed.

A subtree of a node node is node plus every node that is a descendant of node.

</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> [1,null,0,0,1]
<strong>Output:</strong> [1,null,0,null,1]
</pre>

Only the red nodes satisfy the property "every subtree not containing a 1".
The diagram on the right represents the answer.
Example 2:


Input: root = [1,0,1,0,0,0,1]
Output: [1,null,1,null,1]
Example 3:


Input: root = [1,1,0,1,1,0,1,0]
Output: [1,1,0,1,1,null,1]
 

Constraints:

The number of nodes in the tree is in the range [1, 200].
Node.val is either 0 or 1.
