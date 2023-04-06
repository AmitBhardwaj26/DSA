
<h2><a href="https://leetcode.com/problems/number-of-closed-islands/description/">1254. Number of Closed Islands</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given a 2D grid consists of 0s (land) and 1s (water).  An island is a maximal 4-directionally connected group of 0s and a closed island is an island totally (all left, top, right, bottom) surrounded by 1s.

Return the number of closed islands.

 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   grid = [[1,1,1,1,1,1,1,0],[1,0,0,0,0,1,1,0],[1,0,1,0,1,1,1,0],[1,0,0,0,0,1,0,1],[1,1,1,1,1,1,1,0]]
<strong>Output:</strong> 2
</pre>
<pre>
Explanation: Islands in gray are closed because they are completely surrounded by water (group of 1s).
  </pre>
  

Constraints:
<pre>
1 <= grid.length, grid[0].length <= 100
0 <= grid[i][j] <=1
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 class Solution {
public:
    int vis[101][101]={0};
    int DFS(int i,int j, vector<vector<int>>& grid )
    {
        if(i<0 || j<0 || i==grid.size() || j==grid[0].size()) return 0;
        if(vis[i][j]==1 || grid[i][j]==1) return 1;
        
        vis[i][j]=1;
        bool check=1;
        
        return DFS(i-1,j,grid) & DFS(i+1,j,grid) & DFS(i,j-1,grid) & DFS(i,j+1,grid);
        
    }
        
        
    int closedIsland(vector<vector<int>>& grid) {
        int m=grid.size(),n=grid[0].size(),count=0;
       for(int i=0;i<m;i++)
       {
           for(int j=0;j<n;j++)
           {
               if(vis[i][j]==0 && grid[i][j] ==0 &&DFS(i,j,grid))
               {
                  // cout<<i<<" "<<j<<"\n";    
                   count++; 
               }
           }
       }
        return count;
    }
};
 </pre>

