
<h2><a href="https://leetcode.com/problems/number-of-dice-rolls-with-target-sum/description/">1155. Number of Dice Rolls With Target Sum</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
You have n dice and each die has k faces numbered from 1 to k.

Given three integers n, k, and target, return the number of possible ways (out of the kn total ways) to roll the dice so the sum of the face-up numbers equals target. Since the answer may be too large, return it modulo 109 + 7.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> n = 1, k = 6, target = 3
<strong>Output:</strong> 1
</pre>
<pre>
You throw one die with 6 faces.
There is only one way to get a sum of 3.
</pre>
  
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> n = 30, k = 30, target = 500
<strong>Output:</strong>  222616187
</pre>
<pre>
The answer must be returned modulo 109 + 7.
</pre>
 

Constraints:
<pre>
1 <= n, k <= 30
1 <= target <= 1000
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

