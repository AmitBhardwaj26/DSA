
<h2><a href="https://leetcode.com/problems/sum-of-even-numbers-after-queries/">109. Convert Sorted List to Binary Search Tree</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given the head of a singly linked list where elements are sorted in ascending order, convert it to a 
height-balanced
 binary search tree.

 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  head = [-10,-3,0,5,9]
<strong>Output:</strong>  [0,-3,9,-10,null,5]
</pre>
<pre>
Explanation:One possible answer is [0,-3,9,-10,null,5], which represents the shown height balanced BST.
  </pre>
  


Constraints:
<pre>
The number of nodes in head is in the range [0, 2 * 104].
-105 <= Node.val <= 105
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 /**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    TreeNode* constructBST(ListNode *leftHead, ListNode *rightHead) {
        if (leftHead == rightHead)
            return nullptr;
        ListNode *slow = leftHead, *fast = leftHead;
        while (fast != rightHead && fast -> next != rightHead) {
            slow = slow -> next;
            fast = fast -> next -> next;
        }
        TreeNode *root = new TreeNode(slow -> val);
        root -> left = constructBST(leftHead, slow);
        root -> right = constructBST(slow -> next, rightHead);
        return root;
    }
    TreeNode* sortedListToBST(ListNode* head) {
        if (head == nullptr)
            return nullptr;
        if (head -> next == nullptr) {
            TreeNode *root = new TreeNode(head -> val);
            return root;
        }
        return constructBST(head, nullptr);
    }
};
 </pre>

