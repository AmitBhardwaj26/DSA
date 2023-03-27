
<h2><a href="https://leetcode.com/problems/minimum-path-sum/description/">64. Minimum Path Sum</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given a m x n grid filled with non-negative numbers, find a path from top left to bottom right, which minimizes the sum of all numbers along its path.

Note: You can only move either down or right at any point in time.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> grid = [[1,3,1],[1,5,1],[4,2,1]]
<strong>Output:</strong> 7
</pre>
<pre>
Explanation: Because the path 1 → 3 → 1 → 1 → 1 minimizes the sum.
  </pre>
 

Constraints:
<pre>
1 <= nums.length <= 104
-104 <= nums[i] <= 104
1 <= queries.length <= 104
-104 <= vali <= 104
0 <= indexi < nums.length
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
class Solution {
public:
    int dp[201][201];
    int solve(vector<vector<int>>& grid,int i ,int j)
    {
        if(i==grid.size()-1 && j==grid[0].size()-1) return grid[i][j];
        if(i==grid.size() || j==grid[0].size()) return 1110;
         
        if(dp[i][j]!=-1) return dp[i][j];
        
         return dp[i][j]= grid[i][j] +min(solve(grid,i+1,j) , solve(grid,i,j+1));
            
    }
    
    int minPathSum(vector<vector<int>>& grid) {
        memset(dp,-1,sizeof(dp));
        return solve(grid,0,0);
    }
};
 </pre>

