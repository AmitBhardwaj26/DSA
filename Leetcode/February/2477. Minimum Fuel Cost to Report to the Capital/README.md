
<h2><a href="https://leetcode.com/problems/minimum-fuel-cost-to-report-to-the-capital/description/">2477. Minimum Fuel Cost to Report to the Capital</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
There is a tree (i.e., a connected, undirected graph with no cycles) structure country network consisting of n cities numbered from 0 to n - 1 and exactly n - 1 roads. The capital city is city 0. You are given a 2D integer array roads where roads[i] = [ai, bi] denotes that there exists a bidirectional road connecting cities ai and bi.

There is a meeting for the representatives of each city. The meeting is in the capital city.

There is a car in each city. You are given an integer seats that indicates the number of seats in each car.

A representative can use the car in their city to travel or change the car and ride with another representative. The cost of traveling between two cities is one liter of fuel.

Return the minimum number of liters of fuel to reach the capital city.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  roads = [[0,1],[0,2],[0,3]], seats = 5
<strong>Output:</strong> 3
</pre>
<pre>
Explanation:- Representative1 goes directly to the capital with 1 liter of fuel.
- Representative2 goes directly to the capital with 1 liter of fuel.
- Representative3 goes directly to the capital with 1 liter of fuel.
It costs 3 liters of fuel at minimum. 
It can be proven that 3 is the minimum number of liters of fuel needed.
  </pre>
  
Example 2:

Input: nums = [1], queries = [[4,0]]
Output: [0]
 

Constraints:
<pre>
1 <= nums.length <= 104
-104 <= nums[i] <= 104
1 <= queries.length <= 104
-104 <= vali <= 104
0 <= indexi < nums.length
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
        class Solution {
public:
    // vector<int> adj[];
    long long dp[100001];
    int solve(int i,int c, vector<int> adj[])
    {
        long long ans=1;
        if(dp[i]!=-1) return dp[i];
        for(auto it: adj[i])
        {
             if(it!=c) ans+=solve(it,i,adj);
        }
        return dp[i]= ans;
    }
    

    long long minimumFuelCost(vector<vector<int>>& r, int s) {
        int n=r.size();
        int a[n+1];
        
        vector<int> adj[n+1];
        long long ans=0;
        for(int i=0;i<n;i++)
        {
            int u=r[i][0],v=r[i][1];
             adj[u].push_back(v);
             adj[v].push_back(u);
        }
        memset(dp,-1,sizeof(dp));
        
        solve(0,-1,adj);
        for(int i=1;i<=n;i++)
        {
             ans+=ceil((double)dp[i]/s);
        }
        return ans;
    }
};
          
 </pre>

