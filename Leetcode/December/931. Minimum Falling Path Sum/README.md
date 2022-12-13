
<h2><a href="https://leetcode.com/problems/minimum-falling-path-sum/description/">931. Minimum Falling Path Sum</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given an n x n array of integers matrix, return the minimum sum of any falling path through matrix.
A falling path starts at any element in the first row and chooses the element in the next row that is either directly below or diagonally left/right. Specifically, the next element from position (row, col) will be (row + 1, col - 1), (row + 1, col), or (row + 1, col + 1).

 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  matrix = [[2,1,3],[6,5,4],[7,8,9]]
<strong>Output:</strong> 13
</pre>
<pre>
There are two falling paths with a minimum sum as shown.
  </pre>
  

Constraints:
<pre>
n == matrix.length == matrix[i].length
1 <= n <= 100
-100 <= matrix[i][j] <= 100
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
      class Solution {
public:
    int t[102][102];
    
    int solve(vector<vector<int>>& ma, int m, int n)
    {
        // base condition
         if(m==0 ) return 0;
        if(t[m][n]!=-1) return t[m][n];
        
        int ans=0;
         
        if(n==ma[0].size()) ans=ma[m-1][n-1]+ min(solve(ma,m-1,n-1),solve(ma,m-1,n));
        else if(n==1) ans=ma[m-1][n-1] + min(solve(ma,m-1,n+1),solve(ma,m-1,n)); 
        else 
        {
          ans= ma[m-1][n-1] + min(min(solve(ma,m-1,n-1),solve(ma,m-1,n)), solve(ma,m-1,n+1) );
        }
        return t[m][n]= ans;
    }
        
    
    int minFallingPathSum(vector<vector<int>>& matrix) {
       
        int sum=INT_MAX;
        memset(t,-1,sizeof(t));
        for(int i=matrix[0].size(); i>=1; i--)
        {  
        sum=min(sum, solve(matrix, matrix.size(),i));
            cout<<sum<<"\n";
        }
        
        return sum;
    }
};
          
 </pre>

