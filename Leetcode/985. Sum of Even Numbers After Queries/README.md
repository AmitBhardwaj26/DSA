
<h2><a href="https://leetcode.com/problems/sum-of-even-numbers-after-queries/">985. Sum of Even Numbers After Queries</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
 You are given an integer array nums and an array queries where queries[i] = [vali, indexi].

For each query i, first, apply nums[indexi] = nums[indexi] + vali, then print the sum of the even values of nums.

Return an integer array answer where answer[i] is the answer to the ith query.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   nums = [1,2,3,4], queries = [[1,0],[-3,1],[-4,0],[2,3]]
<strong>Output:</strong> [8,6,2,4]
</pre>
<p>
Explanation: At the beginning, the array is [1,2,3,4].
After adding 1 to nums[0], the array is [2,2,3,4], and the sum of even values is 2 + 2 + 4 = 8.
After adding -3 to nums[1], the array is [2,-1,3,4], and the sum of even values is 2 + 4 = 6.
After adding -4 to nums[0], the array is [-2,-1,3,4], and the sum of even values is -2 + 4 = 2.
After adding 2 to nums[3], the array is [-2,-1,3,6], and the sum of even values is -2 + 6 = 4.
  </p>
  
Example 2:

Input: nums = [1], queries = [[4,0]]
Output: [0]
 

Constraints:

1 <= nums.length <= 104
-104 <= nums[i] <= 104
1 <= queries.length <= 104
-104 <= vali <= 104
0 <= indexi < nums.length

<hr>
 <strong><b>Solution</b></strong>
 <br>
 <p><pre>
 class Solution {
public:
    int findLength(vector<int>& nums1, vector<int>& nums2) {
        ios_base::sync_with_stdio(0);
        int n = nums1.size(),m = nums2.size();
        vector<vector<int>>dp(n,vector<int>(m,0));
        for(int i = n-1; i>=0; i--){
            for(int j = m-1; j>=0; j--){
                if(i==n-1 || j==m-1){
                    if(nums1[i]==nums2[j]){
                        dp[i][j] = 1;
                    }
                }
                else{
                    if(nums1[i]==nums2[j]){
                        dp[i][j] = 1+dp[i+1][j+1];
                    }
                }
            }
        }
        int ans = 0;
        for(int i = 0; i<n; i++){
            for(int j = 0; j<m; j++){
                ans = max(ans,dp[i][j]);
            }
        }
        return ans;
    }
};
 </pre>
</p>
