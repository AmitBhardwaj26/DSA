
<h2><a href="https://leetcode.com/problems/sum-of-even-numbers-after-queries/">67. Add Binary</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
 Given two binary strings a and b, return their sum as a binary string.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  a = "11", b = "1"
<strong>Output:</strong>  "100"
</pre>


Constraints:
<pre>
1 <= a.length, b.length <= 104
a and b consist only of '0' or '1' characters.
Each string does not contain leading zeros except for the zero itself.
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

