
<h2><a href="https://leetcode.com/problems/toeplitz-matrix/">766. Toeplitz Matrix</a></h2>
<h3>Easy</h3>
<hr>
<div><p>
Given an m x n matrix, return true if the matrix is Toeplitz. Otherwise, return false.

A matrix is Toeplitz if every diagonal from top-left to bottom-right has the same elements.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>    matrix = [[1,2,3,4],[5,1,2,3],[9,5,1,2]]
<strong>Output:</strong> true
</pre>
<pre>
In the above grid, the diagonals are:
"[9]", "[5, 5]", "[1, 1, 1]", "[2, 2, 2]", "[3, 3]", "[4]".
In each diagonal all elements are the same, so the answer is True.
</pre>

Constraints:
<pre>
m == matrix.length
n == matrix[i].length
1 <= m, n <= 20
0 <= matrix[i][j] <= 99
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
        class Solution {
          public:
               bool isToeplitzMatrix(const vector<vector<int>>& matrix) {
                  const int rows = matrix.size();
                  const int cols = matrix[0].size();
                  for (int r = 1; r < rows; ++r)
                      for (int c = 1; c < cols; ++c)
                          if (matrix[r][c] != matrix[r - 1][c - 1]) return false;

                  return true;
              }
          };
          
 </pre>

