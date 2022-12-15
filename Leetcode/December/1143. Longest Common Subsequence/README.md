
<h2><a href="https://leetcode.com/problems/longest-common-subsequence/description/">1143. Longest Common Subsequence</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
 Given two strings text1 and text2, return the length of their longest common subsequence. If there is no common subsequence, return 0.

A subsequence of a string is a new string generated from the original string with some characters (can be none) deleted without changing the relative order of the remaining characters.

For example, "ace" is a subsequence of "abcde".
A common subsequence of two strings is a subsequence that is common to both strings.
 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   text1 = "abcde", text2 = "ace" 
<strong>Output:</strong> 3
</pre>
<pre>
The longest common subsequence is "ace" and its length is 3.
  </pre>
  
Input: text1 = "abc", text2 = "abc"
Output: 3
Explanation: The longest common subsequence is "abc" and its length is 3.
 

Constraints:
<pre>
1 <= text1.length, text2.length <= 1000
text1 and text2 consist of only lowercase English characters.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
         class Solution {
public:
    int dp[1001][1001];
    string s1,s2;
    int LCS(int n, int m)
    {
        //base case
        if(n==0||m==0) return 0;
        //Memozise
        if(dp[n][m]!=-1) return dp[n][m];
        
        //choice diagram
        int ans=0;
        if(s1[n-1]==s2[m-1]) ans= 1+LCS(n-1,m-1);
        else ans=max(LCS(n-1,m),LCS(n,m-1));
        return dp[n][m]=ans;
    }
    
    int longestCommonSubsequence(string text1, string text2) {
        memset(dp,-1,sizeof(dp));
        s1=text1,s2=text2;
        return LCS(text1.size(),text2.size()); 
    }
};
          
 </pre>

