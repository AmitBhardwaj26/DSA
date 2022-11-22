
<h2><a href="https://leetcode.com/problems/perfect-squares/description/">279. Perfect Squares
</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
 Given an integer n, return the least number of perfect square numbers that sum to n.

A perfect square is an integer that is the square of an integer; in other words, it is the product of some integer with itself. For example, 1, 4, 9, and 16 are perfect squares while 3 and 11 are not.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   n = 12
<strong>Output:</strong> 3
</pre>
<pre>
12 = 4 + 4 + 4.
  </pre>
  


Constraints:
<pre>
1 <= n <= 104
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
         class Solution {
public:
    int dp[10001];
    int solve(int n)
    {
        //base case
        if(n<4) return n;
        
        //memo
        if(dp[n]!=-1) return dp[n];
        
        //choice diagram
        int ans=INT_MAX;
        int x=sqrt(n);
        for(int i=x;i>=2;i--)
        {
            ans=min(ans,1+solve(n-(i*i)));
        }
        return dp[n]=ans;
    }   
        
    
    int numSquares(int n) {
        memset(dp,-1,sizeof(dp));
       return solve(n);  
     }
};
          
 </pre>

