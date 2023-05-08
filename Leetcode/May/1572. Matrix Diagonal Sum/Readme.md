
<h2><a href="https://leetcode.com/problems/matrix-diagonal-sum/description/">1572. Matrix Diagonal Sum</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
 Given a square matrix mat, return the sum of the matrix diagonals.

Only include the sum of all the elements on the primary diagonal and all the elements on the secondary diagonal that are not part of the primary diagonal.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  mat = [[1,2,3], [4,5,6], [7,8,9]]
<strong>Output:</strong> 25
</pre>
<pre>
Explanation: Diagonals sum: 1 + 5 + 9 + 3 + 7 = 25
Notice that element mat[1][1] = 5 is counted only once.
  </pre>
  
Example 2:

Input: nums = [1], queries = [[4,0]]
Output: [0]
 

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
    public int diagonalSum(int[][] mat) {
        int ans=0,n=mat.length;
        for(int i=0;i<n;i++)
        {
            ans+=mat[i][i];
            ans+=mat[i][n-i-1];
        }
        if(n%2==1) return ans-mat[n/2][n/2];
        return ans;
    }
}
 </pre>

