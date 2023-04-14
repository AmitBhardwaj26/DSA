
<h2><a href="https://leetcode.com/problems/longest-palindromic-subsequence/description/">516. Longest Palindromic Subsequence</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given a string s, find the longest palindromic subsequence's length in s.

A subsequence is a sequence that can be derived from another sequence by deleting some or no elements without changing the order of the remaining elements.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   s = "bbbab"
<strong>Output:</strong> 4
</pre>
<pre>
Explanation: One possible longest palindromic subsequence is "bbbb".
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

