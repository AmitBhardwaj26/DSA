
<h2><a href="https://leetcode.com/problems/sum-of-even-numbers-after-queries/">149. Max Points on a Line</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
 Given an array of points where points[i] = [xi, yi] represents a point on the X-Y plane, return the maximum number of points that lie on the same straight line.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  points = [[1,1],[2,2],[3,3]]
<strong>Output:</strong> 3
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
1 <= points.length <= 300
points[i].length == 2
-104 <= xi, yi <= 104
All the points are unique.
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

