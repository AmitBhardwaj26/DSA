
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
              vector<int> sumEvenAfterQueries(vector<int>& nums, vector<vector<int>>& q) {
                  int ans=0;
                  for(int i=0;i<nums.size();i++)
                  {
                      if(nums[i]%2==0) ans+=nums[i];
                  }
                  vector<int> v;
                  for(int i=0;i<q.size();i++)
                  {
                      int val=q[i][0],ind=q[i][1];
                      if(nums[ind]%2==0) ans-=nums[ind];
                      nums[ind]+=val;
                      if(nums[ind]%2==0) ans+=nums[ind];
                      v.push_back(ans);
                  }
                  return v;
              }
          };
          
 </pre>

