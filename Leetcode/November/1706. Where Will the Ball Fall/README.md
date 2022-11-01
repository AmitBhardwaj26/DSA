
<h2><a href="https://leetcode.com/problems/where-will-the-ball-fall/description/">1706. Where Will the Ball Fall</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
You have a 2-D grid of size m x n representing a box, and you have n balls. The box is open on the top and bottom sides.

Each cell in the box has a diagonal board spanning two corners of the cell that can redirect a ball to the right or to the left.

A board that redirects the ball to the right spans the top-left corner to the bottom-right corner and is represented in the grid as 1.
A board that redirects the ball to the left spans the top-right corner to the bottom-left corner and is represented in the grid as -1.
We drop one ball at the top of each column of the box. Each ball can get stuck in the box or fall out of the bottom. A ball gets stuck if it hits a "V" shaped pattern between two boards or if a board redirects the ball into either wall of the box.

Return an array answer of size n where answer[i] is the column that the ball falls out of at the bottom after dropping the ball from the ith column at the top, or -1 if the ball gets stuck in the box.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>    grid = [[1,1,1,-1,-1],[1,1,1,-1,-1],[-1,-1,-1,1,1],[1,1,1,1,-1],[-1,-1,-1,-1,-1]]
<strong>Output:</strong> [1,-1,-1,-1,-1]
</pre>
<pre>
 This example is shown in the photo.
Ball b0 is dropped at column 0 and falls out of the box at column 1.
Ball b1 is dropped at column 1 and will get stuck in the box between column 2 and 3 and row 1.
Ball b2 is dropped at column 2 and will get stuck on the box between column 2 and 3 and row 0.
Ball b3 is dropped at column 3 and will get stuck on the box between column 2 and 3 and row 0.
Ball b4 is dropped at column 4 and will get stuck on the box between column 2 and 3 and row 1.
  </pre>
  
Input: grid = [[1,1,1,1,1,1],[-1,-1,-1,-1,-1,-1],[1,1,1,1,1,1],[-1,-1,-1,-1,-1,-1]]
Output: [0,1,2,3,4,-1]
 

Constraints:
<pre>
m == grid.length
n == grid[i].length
1 <= m, n <= 100
grid[i][j] is 1 or -1.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
       class Solution {
          public:
             int row,col;
             int dfs(int i,int j,vector<vector<int>>& grid)
             {
                 if(i==row) return j;
                 if(i>=row || j>=col) return -1;

                 if(j+1<col && grid[i][j]==1 && grid[i][j+1]==1) return dfs(i+1,j+1,grid);
                  else if(j-1>=0 && grid[i][j]==-1 && grid[i][j-1]==-1) return dfs(i+1,j-1,grid);
                  else return -1;
             }

              vector<int> findBall(vector<vector<int>>& grid) {
                   row=grid.size(),col=grid[0].size();
                  vector<int> ans(col);
                  for(int i=0;i<col;i++)
                  {
                      ans[i]=dfs(0,i,grid);
                  }
                  return ans;
              }
          };
          
 </pre>

