
<h2><a href="https://leetcode.com/problems/sum-of-even-numbers-after-queries/">985. Sum of Even Numbers After Queries</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
A message containing letters from A-Z can be encoded into numbers using the following mapping:

'A' -> "1"
'B' -> "2"
...
'Z' -> "26"
To decode an encoded message, all the digits must be grouped then mapped back into letters using the reverse of the mapping above (there may be multiple ways). For example, "11106" can be mapped into:

"AAJF" with the grouping (1 1 10 6)
"KJF" with the grouping (11 10 6)
Note that the grouping (1 11 06) is invalid because "06" cannot be mapped into 'F' since "6" is different from "06".

Given a string s containing only digits, return the number of ways to decode it.

The test cases are generated so that the answer fits in a 32-bit integer.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   s = "12"
<strong>Output:</strong> 2
</pre>

  
Example 2:

Input:  s = "226"
Output: 3
 

Constraints:
<pre>
1 <= s.length <= 100
s contains only digits and may contain leading zero(s).
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
        class Solution {
public:
    int dp[102];
    int solve(string s,int i)
    {
        if(i>=s.size()  ) return 1;
        if(s[i]=='0') return 0;
         if(dp[i]!=-1) return dp[i];
        
            int x=s[i]-'0'; bool c=0;
        if(i+1<s.size()) {x=x*10 +s[i+1]-'0'; c=1;}
    
        //choice diagram
        if(x<=26 && c) dp[i]= solve(s,i+2)+solve(s,i+1);
        else dp[i]=solve(s,i+1);
        return dp[i];
    }
    
    
    int numDecodings(string s) {
        memset(dp,-1,sizeof(dp));
       return max(0,solve(s,0));
    }
};
 </pre>

