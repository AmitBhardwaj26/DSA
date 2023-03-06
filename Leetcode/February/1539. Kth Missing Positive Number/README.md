
<h2><a href="https://leetcode.com/problems/kth-missing-positive-number/description/">1539. Kth Missing Positive Number</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given an array arr of positive integers sorted in a strictly increasing order, and an integer k.

Return the kth positive integer that is missing from this array.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  arr = [2,3,4,7,11], k = 5
<strong>Output:</strong> [8,6,2,4]
</pre>
<pre>
Explanation:  The missing positive integers are [1,5,6,8,9,10,12,13,...]. The 5th missing positive integer is 9.
  </pre>
  
Example 2:

Input: nums = [1], queries = [[4,0]]
Output: [0]
 

Constraints:
<pre>
1 <= arr.length <= 1000
1 <= arr[i] <= 1000
1 <= k <= 1000
arr[i] < arr[j] for 1 <= i < j <= arr.length
 
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

