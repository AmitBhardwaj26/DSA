
<h2><a href="https://leetcode.com/problems/maximum-value-of-k-coins-from-piles/">2218. Maximum Value of K Coins From Piles</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
There are n piles of coins on a table. Each pile consists of a positive number of coins of assorted denominations.

In one move, you can choose any coin on top of any pile, remove it, and add it to your wallet.

Given a list piles, where piles[i] is a list of integers denoting the composition of the ith pile from top to bottom, and a positive integer k, return the maximum total value of coins you can have in your wallet if you choose exactly k coins optimally.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  piles = [[1,100,3],[7,8,9]], k = 2
<strong>Output:</strong> 101
</pre>
<pre>
Explanation: The above diagram shows the different ways we can choose k coins.
The maximum total we can obtain is 101.
  </pre>
  
Constraints:
<pre>
n == piles.length
1 <= n <= 1000
1 <= piles[i][j] <= 105
1 <= k <= sum(piles[i].length) <= 2000
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

