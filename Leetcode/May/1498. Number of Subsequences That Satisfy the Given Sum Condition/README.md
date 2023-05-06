
<h2><a href="https://leetcode.com/problems/number-of-subsequences-that-satisfy-the-given-sum-condition/">1498. Number of Subsequences That Satisfy the Given Sum Condition</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
You are given an array of integers nums and an integer target.

Return the number of non-empty subsequences of nums such that the sum of the minimum and maximum element on it is less or equal to target. Since the answer may be too large, return it modulo 109 + 7.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   nums = [3,5,6,7], target = 9
<strong>Output:</strong> 4
</pre>
<pre>
Explanation: There are 4 subsequences that satisfy the condition.
[3] -> Min value + max value <= target (3 + 3 <= 9)
[3,5] -> (3 + 5 <= 9)
[3,5,6] -> (3 + 6 <= 9)
[3,6] -> (3 + 6 <= 9)
  </pre>
 

Constraints:
<pre>
1 <= nums.length <= 105
1 <= nums[i] <= 106
1 <= target <= 106
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

