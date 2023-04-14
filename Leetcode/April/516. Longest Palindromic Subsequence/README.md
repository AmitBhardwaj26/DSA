
<h2><a href="https://leetcode.com/problems/longest-palindromic-subsequence/description/">516. Longest Palindromic Subsequence</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given a string s, find the longest palindromic subsequence's length in s.

A subsequence is a sequence that can be derived from another sequence by deleting some or no elements without changing the order of the remaining elements.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   s = "bbbab"
<strong>Output:</strong> [8,6,2,4]
</pre>
<pre>
Explanation: At the beginning, the array is [1,2,3,4].
After adding 1 to nums[0], the array is [2,2,3,4], and the sum of even values is 2 + 2 + 4 = 8.
After adding -3 to nums[1], the array is [2,-1,3,4], and the sum of even values is 2 + 4 = 6.
After adding -4 to nums[0], the array is [-2,-1,3,4], and the sum of even values is -2 + 4 = 2.
After adding 2 to nums[3], the array is [-2,-1,3,6], and the sum of even values is -2 + 6 = 4.
  </pre>
  

Constraints:
<pre>
1 <= s.length <= 1000
s consists only of lowercase English letters.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 class Solution {
public:
    
    int solve(string s1,string s2)
    {
        int dp[1002][1002];
        int n=s1.size();
        for(int i=0;i<=n;i++) for(int j=0;j<=n;j++) if(i==0 || j==0) dp[i][j]=0;
        for(int i=1;i<=n;i++) 
        for(int j=1;j<=n;j++) 
        {
            if(s1[i-1]==s2[j-1]) dp[i][j]=1+dp[i-1][j-1];
            else  dp[i][j]=max(dp[i-1][j],dp[i][j-1]);
        }
        
        return dp[n][n];
    }
    
    
    int longestPalindromeSubseq(string s) {
      // memset(dp,-1,sizeof(dp));
        string s1=s;
        reverse(s.begin(),s.end());
        return solve(s,s1);
    }
};
 </pre>

