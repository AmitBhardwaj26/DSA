
<h2><a href="https://leetcode.com/problems/count-good-nodes-in-binary-tree/">1448. Count Good Nodes in Binary Tree</a></h2>
<h3>Medium</h3>
<hr>
<div><p>Given a binary tree root, a node X in the tree is named good if in the path from root to X there are no nodes with a value greater than X.

Return the number of good nodes in the binary tree.

</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> [3,1,4,3,null,1,5]
<strong>Output:</strong> 4
</pre>

 
 <p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> root = [3,3,null,4,2]
<strong>Output:</strong> 3
</pre>

Example 3:

Input: root = [1]
Output: 1
Explanation: Root is considered as good.
 

Constraints:

The number of nodes in the binary tree is in the range [1, 10^5].
Each node's value is between [-10^4, 10^4].
