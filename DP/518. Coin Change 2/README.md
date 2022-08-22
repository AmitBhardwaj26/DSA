<h2><a href="https://leetcode.com/problems/coin-change-2/">72. Edit Distance</a></h2>
<h3>Medium</h3>
<hr>
<div><p>You are given an integer array coins representing coins of different denominations and an integer amount representing a total amount of money.

Return the number of combinations that make up that amount. If that amount of money cannot be made up by any combination of the coins, return 0.

You may assume that you have an infinite number of each kind of coin.

The answer is guaranteed to fit into a signed 32-bit integer.
 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> Input: amount = 5, coins = [1,2,5]
<strong>Output:</strong> 4
</pre>
  
5=5
5=2+2+1
5=2+1+1+1
5=1+1+1+1+1

Example 2:

Input: amount = 3, coins = [2]
Output: 0
Explanation: the amount of 3 cannot be made up just with coins of 2.
  
Example 3:

Input: amount = 10, coins = [10]
Output: 1
