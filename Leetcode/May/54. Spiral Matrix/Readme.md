
<h2><a href="https://leetcode.com/problems/spiral-matrix/description/">54. Spiral Matrix</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
 Given an m x n matrix, return all elements of the matrix in spiral order.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  matrix = [[1,2,3],[4,5,6],[7,8,9]]
<strong>Output:</strong> [1,2,3,6,9,8,7,4,5]
</pre>
<pre>
Explanation: At the beginning, the array is [1,2,3,4].
After adding 1 to nums[0], the array is [2,2,3,4], and the sum of even values is 2 + 2 + 4 = 8.
After adding -3 to nums[1], the array is [2,-1,3,4], and the sum of even values is 2 + 4 = 6.
After adding -4 to nums[0], the array is [-2,-1,3,4], and the sum of even values is -2 + 4 = 2.
After adding 2 to nums[3], the array is [-2,-1,3,6], and the sum of even values is -2 + 6 = 4.
  </pre>
  
 

Constraints:
<pre>
m == matrix.length
n == matrix[i].length
1 <= m, n <= 10
-100 <= matrix[i][j] <= 100
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 class Solution {
public:
    vector<int> spiralOrder(vector<vector<int>>& matrix) {
        int m=matrix.size(),n=matrix[0].size();
        if(m==1) return matrix[0];
        vector<int> ans;
        int si =m*n;
        int c=0;
        if(n==1) 
        {
            for(int i=0;i<m;i++) ans.push_back(matrix[i][0]);
            return ans;
         }

        int rs=0,cs=0,ce=n-1,re=m-1,ccs=0;
        while(rs<=re && cs<=ce)
        {
            for(int i=rs;i<ce;i++) ans.push_back(matrix[rs][i]);
            rs++;
            for(int i=cs;i<re;i++) ans.push_back(matrix[i][ce]);
            cs++;
            for(int i=ce;i>=rs;i--) ans.push_back(matrix[re][i]);
            ce--;
            for(int i=re;i>=rs;i--) ans.push_back(matrix[i][ccs]);
              ccs++; re--;  
        }
        ans.push_back(matrix[m/2][n/2]);
       while(ans.size()>si) ans.pop_back();
        return ans;
    }
};
 </pre>

