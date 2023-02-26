
<h2><a href="https://leetcode.com/problems/edit-distance/description/">72. Edit Distance</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
 Given two strings word1 and word2, return the minimum number of operations required to convert word1 to word2.

You have the following three operations permitted on a word:

Insert a character
Delete a character
Replace a character
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   word1 = "horse", word2 = "ros"
<strong>Output:</strong> 3
</pre>
<pre>
Explanation: horse -> rorse (replace 'h' with 'r')
rorse -> rose (remove 'r')
rose -> ros (remove 'e')
  </pre>
 

Constraints:
<pre>
0 <= word1.length, word2.length <= 500
word1 and word2 consist of lowercase English letters.
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

