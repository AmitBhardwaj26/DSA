
<h2><a href="https://leetcode.com/problems/sum-of-even-numbers-after-queries/">886. Possible Bipartition</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
 We want to split a group of n people (labeled from 1 to n) into two groups of any size. Each person may dislike some other people, and they should not go into the same group.

Given the integer n and the array dislikes where dislikes[i] = [ai, bi] indicates that the person labeled ai does not like the person labeled bi, return true if it is possible to split everyone into two groups in this way.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  n = 4, dislikes = [[1,2],[1,3],[2,4]]
<strong>Output:</strong>  true
</pre>
<pre>
group1 [1,4] and group2 [2,3].
  </pre>
 
Input: n = 3, dislikes = [[1,2],[1,3],[2,3]]
Output: false
 

Constraints:
<pre>
1 <= n <= 2000
0 <= dislikes.length <= 104
dislikes[i].length == 2
1 <= dislikes[i][j] <= n
ai < bi
All the pairs of dislikes are unique.
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

