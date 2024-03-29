
<h2><a href="https://leetcode.com/problems/uncrossed-lines/description/">1035. Uncrossed Lines</a></h2>
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
<pre><strong>Input:</strong>   nums1 = [2,5,1,2,5], nums2 = [10,5,2,1,5,2]
<strong>Output:</strong>3
</pre>
<pre>

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

