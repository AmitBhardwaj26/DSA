
<h2><a href="https://leetcode.com/problems/minimum-insertion-steps-to-make-a-string-palindrome/description/">1312. Minimum Insertion Steps to Make a String Palindrome</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given a string s. In one step you can insert any character at any index of the string.

Return the minimum number of steps to make s palindrome.

A Palindrome String is one that reads the same backward as well as forward.

 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   s = "zzazz"
<strong>Output:</strong> 0
</pre>
<pre>
Explanation: The string "zzazz" is already palindrome we do not need any insertions.
  </pre>
 

Constraints:
<pre>
1 <= s.length <= 500
s consists of lowercase English letters.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
   class Solution {
public:
    string s1,s2;
      int dp[1001][1001];
     int LCS(int n,int m)
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

    int minInsertions(string s) {
          memset(dp,-1,sizeof(dp));
        int n=s.size(); 
        s1=s;
        s2=s;
        reverse(s2.begin(),s2.end());
        return n-LCS(n,n);
    }
};
 </pre>

