
<h2><a href="https://leetcode.com/problems/jump-game-ii/description/">45. Jump Game II</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
You are given a 0-indexed array of integers nums of length n. You are initially positioned at nums[0].

Each element nums[i] represents the maximum length of a forward jump from index i. In other words, if you are at nums[i], you can jump to any nums[i + j] where:

0 <= j <= nums[i] and
i + j < n
Return the minimum number of jumps to reach nums[n - 1]. The test cases are generated such that you can reach nums[n - 1].
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   nums = [2,3,1,1,4]
<strong>Output:</strong>  2
</pre>
<pre>
Explanation: The minimum number of jumps to reach the last index is 2. Jump 1 step from index 0 to 1, then 3 steps to the last index.
  </pre>
  


Constraints:
<pre>
1 <= nums.length <= 104
0 <= nums[i] <= 1000
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
         // brute force Memoization in dp
class Solution {
public:
         
    int solve(vector<int> &v,int m, int count, vector<int> &dp )
    {
        //base condition
        if(m>=v.size()-1) return 0;
        
        // check
        if(dp[m]!=-1) return dp[m];
        
        //choice diagram
        int ans=10001;
        for(int i=1;i<=v[m];i++)
        {
          ans=min(ans,1+solve(v,m+i,count+1,dp));  
        }
        return dp[m]=ans; 
    }
    
    int jump(vector<int>& nums) {
        
        vector<int> dp(nums.size(),-1);
        return solve(nums,0,0,dp);
        
    }
};
          
 </pre>

