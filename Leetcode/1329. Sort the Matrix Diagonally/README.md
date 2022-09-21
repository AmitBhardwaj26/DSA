
<h2><a href="https://leetcode.com/problems/sort-the-matrix-diagonally/">1329. Sort the Matrix Diagonally</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
    
A matrix diagonal is a diagonal line of cells starting from some cell in either the topmost row or leftmost column and going in the bottom-right direction until reaching the matrix's end. For example, the matrix diagonal starting from mat[2][0], where mat is a 6 x 3 matrix, includes cells mat[2][0], mat[3][1], and mat[4][2].

Given an m x n matrix mat of integers, sort each matrix diagonal in ascending order and return the resulting matrix.

</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   mat = [[3,3,1,1],[2,2,1,2],[1,1,1,2]]
<strong>Output:</strong> [[1,1,1,1],[1,2,2,2],[1,2,3,3]]
</pre>
  
Example 2:

Input: mat = [[11,25,66,1,69,7],[23,55,17,45,15,52],[75,31,36,44,58,8],[22,27,33,25,68,4],[84,28,14,11,5,50]]
Output: [[5,17,4,1,52,7],[11,11,25,45,8,69],[14,23,25,44,58,15],[22,27,31,36,50,66],[84,28,75,33,55,68]]

Constraints:
    
<pre>
m == mat.length
n == mat[i].length
1 <= m, n <= 100
1 <= mat[i][j] <= 100
</pre>
    
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
       class Solution {
public:
    vector<vector<int>> diagonalSort(vector<vector<int>>& mat) {
        int n=mat.size(),m=mat[0].size(); 
      
        for(int j=0;j<m;j++)
        {
              vector<int> v;
            int x=0,y=j,index=0;
            while(x<n && y<m)
            {
                v.push_back(mat[x][y]);
                x+=1,y+=1;
            }
            sort(v.begin(),v.end());
            x=0,y=j; 
            while(x<n && y<m && index<v.size())
            {
               mat[x][y]=v[index++];
                x++,y++;
            }
        }
       for(int i=1;i<n;i++)
        {
             vector<int> v;
            int x=i,y=0,index=0;
            while(x<n && y<m)
            {
                v.push_back(mat[x][y]);
                x+=1,y+=1;
            }
            sort(v.begin(),v.end());
            x=i,y=0; 
            while(x<n && y<m && index<v.size())
            {
               mat[x][y]=v[index++];
                x++,y++;
            }
        }
            return mat;
    }
};
 </pre>

