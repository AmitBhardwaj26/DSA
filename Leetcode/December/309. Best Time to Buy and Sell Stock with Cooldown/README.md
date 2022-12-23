
<h2><a href="https://leetcode.com/problems/sum-of-even-numbers-after-queries/">985. Sum of Even Numbers After Queries</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
You are given an array prices where prices[i] is the price of a given stock on the ith day.

Find the maximum profit you can achieve. You may complete as many transactions as you like (i.e., buy one and sell one share of the stock multiple times) with the following restrictions:

After you sell your stock, you cannot buy stock on the next day (i.e., cooldown one day).
Note: You may not engage in multiple transactions simultaneously (i.e., you must sell the stock before you buy again).
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   prices = [1,2,3,0,2]
<strong>Output:</strong> 3
</pre>
<pre>
transactions = [buy, sell, cooldown, buy, sell]
  </pre>
  

 

Constraints:
<pre>
1 <= prices.length <= 5000
0 <= prices[i] <= 1000
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 class Solution {
public:
    int dp[5001][2];
    int solve(vector<int> &v , int n ,bool c)
    {
        if(n>=v.size()) return 0;
        
        if(dp[n][c]!=-1) return dp[n][c];
        
        int a=INT_MIN,b=INT_MIN;
        if(c)
        a= max(-v[n]+ solve(v,n+1,0) ,solve(v,n+1,1) );
        else 
        {
         b=max(v[n]+solve(v,n+2,1),solve(v,n+1,0) );
           // ans=max(ans,b);
        }
        return dp[n][c]=max(a,b);
    }
    
    int maxProfit(vector<int>& prices) {
        memset(dp,-1,sizeof(dp));
       return solve(prices,0,1);
        //return ans;
    }
};
          
 </pre>

