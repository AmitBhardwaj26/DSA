
<h2><a href="https://leetcode.com/problems/ipo/description/">502. IPO</a></h2>
<h3>Hard</h3>
<hr>
<div><p>
Suppose LeetCode will start its IPO soon. In order to sell a good price of its shares to Venture Capital, LeetCode would like to work on some projects to increase its capital before the IPO. Since it has limited resources, it can only finish at most k distinct projects before the IPO. Help LeetCode design the best way to maximize its total capital after finishing at most k distinct projects.

You are given n projects where the ith project has a pure profit profits[i] and a minimum capital of capital[i] is needed to start it.

Initially, you have w capital. When you finish a project, you will obtain its pure profit and the profit will be added to your total capital.

Pick a list of at most k distinct projects from given projects to maximize your final capital, and return the final maximized capital.

The answer is guaranteed to fit in a 32-bit signed integer.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>    k = 2, w = 0, profits = [1,2,3], capital = [0,1,1]
<strong>Output:</strong>  4
</pre>
<pre>
Explanation:  Since your initial capital is 0, you can only start the project indexed 0.
After finishing it you will obtain profit 1 and your capital becomes 1.
With capital 1, you can either start the project indexed 1 or the project indexed 2.
Since you can choose at most 2 projects, you need to finish the project indexed 2 to get the maximum capital.
Therefore, output the final maximized capital, which is 0 + 1 + 3 = 4.
  </pre>
  

 

Constraints:
<pre>
1 <= k <= 105
0 <= w <= 109
n == profits.length
n == capital.length
1 <= n <= 105
0 <= profits[i] <= 104
0 <= capital[i] <= 109
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
    class Solution {
public:
    int findMaximizedCapital(int k, int w, vector<int>& profit, vector<int>& capital) {
        int n=profit.size();
        vector<pair<int,int>> v;
        for(int i=0;i<n;i++)
        {
            v.push_back({ capital[i] , profit[i] });
        }
        sort(v.begin(),v.end());

        priority_queue<int> pq;
        int ans=w;
        for(int i=0;i<n;i++)
        {
            while(v[i].first>w && k>0 && pq.size()>0)
            {
                    w+=pq.top(); pq.pop(); k--;
            }
            if(v[i].first<=w) pq.push(v[i].second);
        }  
        while(k-- && pq.size()>0)
        {
            w+=pq.top(); pq.pop();
        }
        return w;     
    }
};
 </pre>

