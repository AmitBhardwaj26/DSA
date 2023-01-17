
<h2><a href="https://leetcode.com/problems/sum-of-even-numbers-after-queries/">926. Flip String to Monotone Increasing</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
A binary string is monotone increasing if it consists of some number of 0's (possibly none), followed by some number of 1's (also possibly none).

You are given a binary string s. You can flip s[i] changing it from 0 to 1 or from 1 to 0.

Return the minimum number of flips to make s monotone increasing.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  s = "00110"
<strong>Output:</strong> 1
</pre>
<pre>
Explanation: We flip the last digit to get 00111.
  </pre>
  

Constraints:
<pre>
1 <= s.length <= 105
s[i] is either '0' or '1'.
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

