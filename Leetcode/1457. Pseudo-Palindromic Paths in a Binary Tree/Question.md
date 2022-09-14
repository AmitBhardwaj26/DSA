
<h2><a href="https://leetcode.com/problems/pseudo-palindromic-paths-in-a-binary-tree/">1457. Pseudo-Palindromic Paths in a Binary Tree</a></h2>
<h3>Medium</h3>
<hr>
<div><p>Given a binary tree where node values are digits from 1 to 9. A path in the binary tree is said to be pseudo-palindromic if at least one permutation of the node values in the path is a palindrome.

Return the number of pseudo-palindromic paths going from the root node to leaf nodes.

</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> root = [2,3,1,3,1,null,1]
<strong>Output:</strong>  2 
</pre>
Example 2:



Input: root = [2,1,1,1,3,null,null,null,null,null,1]
Output: 1 
Explanation: The figure above represents the given binary tree. There are three paths going from the root node to leaf nodes: the green path [2,1,1], the path [2,1,3,1], and the path [2,1]. Among these paths only the green path is pseudo-palindromic since [2,1,1] can be rearranged in [1,2,1] (palindrome).
Example 3:

Input: root = [9]
Output: 1
 

Constraints:

The number of nodes in the tree is in the range [1, 105].
1 <= Node.val <= 9
