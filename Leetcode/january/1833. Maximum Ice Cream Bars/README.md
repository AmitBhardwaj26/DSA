
<h2><a href="https://leetcode.com/problems/maximum-ice-cream-bars/description/">1833. Maximum Ice Cream Bars</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
It is a sweltering summer day, and a boy wants to buy some ice cream bars.

At store, there are n ice cream bars. You are given an array costs of length n, where costs[i] is the price of the ith ice cream bar in coins. The boy initially has coins coins to spend, and he wants to buy as many ice cream bars as possible. 

Return the maximum number of ice cream bars the boy can buy with coins coins.

Note: The boy can buy the ice cream bars in any order.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   costs = [1,3,2,4,1], coins = 7
<strong>Output:</strong>4
</pre>
<pre>
Explanation:The boy can buy ice cream bars at indices 0,1,2,4 for a total price of 1 + 3 + 2 + 1 = 7.
  </pre>
  


Constraints:
<pre>
costs.length == n
1 <= n <= 105
1 <= costs[i] <= 105
1 <= coins <= 108
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
 class Solution {
    public:
        int maxIceCream(vector<int>& cost, int coins) {
            sort(cost.begin(),cost.end());
            int ans=0,n=cost.size();
            for(int i=0;i<n;i++)
            {
               if(cost[i]<=coins) 
               {
                   ans++; coins-=cost[i];
               }
               else return ans;
            }
            return ans;
        }
    };
          
 </pre>

