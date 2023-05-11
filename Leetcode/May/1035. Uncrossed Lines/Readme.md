
<h2><a href="https://leetcode.com/problems/sum-of-even-numbers-after-queries/">985. Sum of Even Numbers After Queries</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
You are given two integer arrays nums1 and nums2. We write the integers of nums1 and nums2 (in the order they are given) on two separate horizontal lines.

We may draw connecting lines: a straight line connecting two numbers nums1[i] and nums2[j] such that:

nums1[i] == nums2[j], and
the line we draw does not intersect any other connecting (non-horizontal) line.
Note that a connecting line cannot intersect even at the endpoints (i.e., each number can only belong to one connecting line).

Return the maximum number of connecting lines we can draw in this way.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   nums = [1,2,3,4], queries = [[1,0],[-3,1],[-4,0],[2,3]]
<strong>Output:</strong> [8,6,2,4]
</pre>
<pre>
Explanation: At the beginning, the array is [1,2,3,4].
After adding 1 to nums[0], the array is [2,2,3,4], and the sum of even values is 2 + 2 + 4 = 8.
After adding -3 to nums[1], the array is [2,-1,3,4], and the sum of even values is 2 + 4 = 6.
After adding -4 to nums[0], the array is [-2,-1,3,4], and the sum of even values is -2 + 4 = 2.
After adding 2 to nums[3], the array is [-2,-1,3,6], and the sum of even values is -2 + 6 = 4.
  </pre>
  
Example 2:

Input: nums = [1], queries = [[4,0]]
Output: [0]
 

Constraints:
<pre>
1 <= nums.length <= 104
-104 <= nums[i] <= 104
1 <= queries.length <= 104
-104 <= vali <= 104
0 <= indexi < nums.length
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 class Solution {
public:
    int c(vector<int>&v1,vector<int>&v2,int i,int j,vector<vector<int>>&dp){
        if(i>=v1.size() || j>=v2.size())return 0;
        if(dp[i][j]!=-1)return dp[i][j];
        int ans=0;
        if(v1[i]==v2[j]){
            ans=1+c(v1,v2,i+1,j+1,dp);
        }
        ans=max({ans,c(v1,v2,i+1,j,dp),c(v1,v2,i,j+1,dp)});
        dp[i][j]=ans;
        return ans;
    }
    int maxUncrossedLines(vector<int>&v1, vector<int>& v2) {
        vector<vector<int>>dp(v1.size(),vector<int>(v2.size(),-1));
        return c(v1,v2,0,0,dp);
    }
};
 </pre>

