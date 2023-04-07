
<h2><a href="https://leetcode.com/problems/number-of-enclaves/">1020. Number of Enclaves</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
You are given an m x n binary matrix grid, where 0 represents a sea cell and 1 represents a land cell.

A move consists of walking from one land cell to another adjacent (4-directionally) land cell or walking off the boundary of the grid.

Return the number of land cells in grid for which we cannot walk off the boundary of the grid in any number of moves.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  grid = [[0,0,0,0],[1,0,1,0],[0,1,1,0],[0,0,0,0]]
<strong>Output:</strong> 3
</pre>
<pre>
Explanation: There are three 1s that are enclosed by 0s, and one 1 that is not enclosed because its on the boundary.
  </pre>
 

Constraints:
<pre>
m == grid.length
n == grid[i].length
1 <= m, n <= 500
grid[i][j] is either 0 or 1.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 // traverse in all four sides of rectangle if any value is 1 then mark dfs on it and count all corner ones substract it with all one to get the ans

class Solution {
public:
    int vis[501][501]={0};
    int DFS(int i,int j,vector<vector<int>>& grid)
    {
        vis[i][j]=1;
        int count=1;
        if(i-1>=0 && grid[i-1][j]==1 && vis[i-1][j]==0)
           count+= DFS(i-1,j,grid);
        if(j-1>=0 && grid[i][j-1]==1 && vis[i][j-1]==0)
           count+= DFS(i,j-1,grid);
        if(i+1<grid.size() && grid[i+1][j]==1 && vis[i+1][j]==0)
           count+= DFS(i+1,j,grid);
        if(j+1<grid[0].size() && grid[i][j+1]==1 && vis[i][j+1]==0)
           count+= DFS(i,j+1,grid);
       return count; 
    }
    
    int numEnclaves(vector<vector<int>>& grid) {
        int m=grid.size(),n=grid[0].size(),ans=0,one=0;
        
        for(int i=0;i<m;i++)
        {
            for(int j=0;j<n;j++)
            {
                if(grid[i][j]==1) one++;
                if((i==0 || j==0 || i==m-1 || j==n-1) &&
                   vis[i][j]==0 && grid[i][j]==1)
               { ans+=DFS(i,j,grid);  }
            }
        }
        return one-ans;
    }
};
 </pre>

