
<h2><a href="https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/">121. Best Time to Buy and Sell Stock</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
You are given an array prices where prices[i] is the price of a given stock on the ith day.

You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock.

Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return 0.

 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>    prices = [7,1,5,3,6,4]
<strong>Output:</strong> 5
</pre>
<pre>
Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
Note that buying on day 2 and selling on day 1 is not allowed because you must buy before you sell.
  </pre>
 
 

Constraints:
<pre>
1 <= prices.length <= 105
0 <= prices[i] <= 104
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 class Solution {
public:
    int maxProfit(vector<int>& a) {
       int ans=0;
        int x=INT_MAX;
        for(int i=0;i<a.size();i++)
        {
           x=min(a[i],x);
            ans=max((a[i]-x),ans);
        }
        return ans;
    }
};
 </pre>

