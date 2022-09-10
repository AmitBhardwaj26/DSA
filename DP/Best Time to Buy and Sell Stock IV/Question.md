
<h2><a href="https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/">Best Time to Buy and Sell Stock IV</a></h2>
<h3>Hard</h3>
<hr>
<div><p>You are given an integer array prices where prices[i] is the price of a given stock on the ith day, and an integer k.

Find the maximum profit you can achieve. You may complete at most k transactions.

Note: You may not engage in multiple transactions simultaneously (i.e., you must sell the stock before you buy again).
 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> k = 2, prices = [2,4,1]
<strong>Output:</strong> 2
</pre>
  Explanation: Buy on day 1 (price = 2) and sell on day 2 (price = 4), profit = 4-2 = 2.

Example 2:

Input: k = 2, prices = [3,2,6,5,0,3]
Output: 7
Explanation: Buy on day 2 (price = 2) and sell on day 3 (price = 6), profit = 6-2 = 4. Then buy on day 5 (price = 0) and sell on day 6 (price = 3), profit = 3-0 = 3.
 

Constraints:

0 <= k <= 100
0 <= prices.length <= 1000
0 <= prices[i] <= 1000
