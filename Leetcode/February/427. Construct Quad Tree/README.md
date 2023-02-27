
<h2><a href="https://leetcode.com/problems/sum-of-even-numbers-after-queries/">985. Sum of Even Numbers After Queries</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given a n * n matrix grid of 0's and 1's only. We want to represent the grid with a Quad-Tree.

Return the root of the Quad-Tree representing the grid.

Notice that you can assign the value of a node to True or False when isLeaf is False, and both are accepted in the answer.

A Quad-Tree is a tree data structure in which each internal node has exactly four children. Besides, each node has two attributes:

val: True if the node represents a grid of 1's or False if the node represents a grid of 0's.
isLeaf: True if the node is leaf node on the tree or False if the node has the four children.
class Node {
    public boolean val;
    public boolean isLeaf;
    public Node topLeft;
    public Node topRight;
    public Node bottomLeft;
    public Node bottomRight;
}
We can construct a Quad-Tree from a two-dimensional area using the following steps:

If the current grid has the same value (i.e all 1's or all 0's) set isLeaf True and set val to the value of the grid and set the four children to Null and stop.
If the current grid has different values, set isLeaf to False and set val to any value and divide the current grid into four sub-grids as shown in the photo.
Recurse for each of the children with the proper sub-grid.

If you want to know more about the Quad-Tree, you can refer to the wiki.

Quad-Tree format:

The output represents the serialized format of a Quad-Tree using level order traversal, where null signifies a path terminator where no node exists below.

It is very similar to the serialization of the binary tree. The only difference is that the node is represented as a list [isLeaf, val].

If the value of isLeaf or val is True we represent it as 1 in the list [isLeaf, val] and if the value of isLeaf or val is False we represent it as 0.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   grid = [[0,1],[1,0]]
Output: [[0,1],[1,0],[1,1],[1,1],[1,0]]
<strong>Output:</strong> [8,6,2,4]
</pre>
<pre>
Explanation: The explanation of this example is shown below:
Notice that 0 represnts False and 1 represents True in the photo representing the Quad-Tree.
  </pre>
 

Constraints:
<pre>
n == grid.length == grid[i].length
n == 2x where 0 <= x <= 6
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
    
class Solution {
 public:
  Node* construct(vector<vector<int>>& grid) {
    return helper(grid, 0, 0, grid.size());
  }

 private:
  Node* helper(const vector<vector<int>>& grid, int i, int j, int w) {
    if (allSame(grid, i, j, w))
      return new Node(grid[i][j], true);

    Node* node = new Node(true, false);
    node->topLeft = helper(grid, i, j, w / 2);
    node->topRight = helper(grid, i, j + w / 2, w / 2);
    node->bottomLeft = helper(grid, i + w / 2, j, w / 2);
    node->bottomRight = helper(grid, i + w / 2, j + w / 2, w / 2);
    return node;
  }

  bool allSame(const vector<vector<int>>& grid, int i, int j, int w) {
    return all_of(begin(grid) + i, begin(grid) + i + w,
                  [&](const vector<int>& row) {
      return all_of(begin(row) + j, begin(row) + j + w,
                    [&](int num) { return num == grid[i][j]; });
    });
  }
};
 </pre>

