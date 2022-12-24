
<h2><a href="https://leetcode.com/problems/domino-and-tromino-tiling/description/">985. Sum of Even Numbers After Queries</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
You have two types of tiles: a 2 x 1 domino shape and a tromino shape. You may rotate these shapes.


Given an integer n, return the number of ways to tile an 2 x n board. Since the answer may be very large, return it modulo 109 + 7.

In a tiling, every square must be covered by a tile. Two tilings are different if and only if there are two 4-directionally adjacent cells on the board such that exactly one of the tilings has both squares occupied by a tile.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>    n = 3
<strong>Output:</strong> 5
</pre>
<pre>
The five different ways are show above.
  </pre>
  
Example 2:

Input: nums = [1], queries = [[4,0]]
Output: [0]
 

Constraints:
<pre>
1 <= n <= 1000
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
         
class Solution {
public:
     #define ll long long
    #define MOD 1000000007
    int numTilings(int n) {
        vector<ll> dp(n+1);
        iota(dp.begin(),dp.end(),0);
        dp[0] = 1;
        for(int i=3;i<=n;i++)
            dp[i] = (dp[i-1]+dp[i-1]+dp[i-3])%MOD;
        return dp.back();
    }
};
          
 </pre>

