
<h2><a href="https://leetcode.com/problems/as-far-from-land-as-possible/description/">1162. As Far from Land as Possible</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given an n x n grid containing only values 0 and 1, where 0 represents water and 1 represents land, find a water cell such that its distance to the nearest land cell is maximized, and return the distance. If no land or water exists in the grid, return -1.

The distance used in this problem is the Manhattan distance: the distance between two cells (x0, y0) and (x1, y1) is |x0 - x1| + |y0 - y1|.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   grid = [[1,0,1],[0,0,0],[1,0,1]]
<strong>Output:</strong> 2
</pre>
<pre>
Explanation: The cell (1, 1) is as far as possible from all the land with distance 2.
  </pre>
 

Constraints:
<pre>
n == grid.length
n == grid[i].length
1 <= n <= 100
grid[i][j] is 0 or 1
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
          //point 1: All grid type of questions try to do BFS not DFS
//point 2:In which we have to traverse in each directions try to make a directions array
//point 3: make queue of vectors insteed of pair and all

class Solution {
public:
        
      int maxDistance(vector<vector<int>>& grid) {
          int n=grid.size(),m=grid[0].size(),zero=0,one=0;

          queue<vector<int>> q;
          for(int i=0;i<m;i++)
              for(int j=0;j<n;j++)
                if(grid[i][j]==0) zero++,grid[i][j]=INT_MAX;
                else one++,q.push({i,j}), grid[i][j]=0;

          if(one ==n*m || zero==n*m) return -1;

          int dis[][2]={{-1,0},{1,0},{0,-1},{0,1}};
          while(!q.empty())
          {
              int x=q.front()[0],y=q.front()[1];
              q.pop();
              for(int i=0;i<4;i++)
              {
                  int X=x+dis[i][0],Y=y+dis[i][1];
                  if(X<0 || Y<0 || X>=m || Y>=n) continue;
                  if(grid[X][Y]> grid[x][y]+1)
                  {
                      grid[X][Y]= grid[x][y]+1;
                          q.push({X,Y});
                  }
              }   
          }

          int ans=-1;
          for(int i=0;i<m;i++) for(int j=0;j<n;j++)             
               ans=max(ans,grid[i][j]);

          return ans;
      }
};
          
 </pre>

