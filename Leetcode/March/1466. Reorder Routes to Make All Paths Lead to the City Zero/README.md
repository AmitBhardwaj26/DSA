
<h2><a href="https://leetcode.com/problems/reorder-routes-to-make-all-paths-lead-to-the-city-zero/description/"></a></h2>
<h3>Medium</h3>
<hr>
<div><p>
There are n cities numbered from 0 to n - 1 and n - 1 roads such that there is only one way to travel between two different cities (this network form a tree). Last year, The ministry of transport decided to orient the roads in one direction because they are too narrow.

Roads are represented by connections where connections[i] = [ai, bi] represents a road from city ai to city bi.

This year, there will be a big event in the capital (city 0), and many people want to travel to this city.

Your task consists of reorienting some roads such that each city can visit the city 0. Return the minimum number of edges changed.

It's guaranteed that each city can reach city 0 after reorder.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  n = 6, connections = [[0,1],[1,3],[2,3],[4,0],[4,5]]
<strong>Output:</strong> 3
</pre>
<pre>
Explanation: Change the direction of edges show in red such that each node can reach the node 0 (capital).
  </pre>


Constraints:
<pre>
2 <= n <= 5 * 104
connections.length == n - 1
connections[i].length == 2
0 <= ai, bi <= n - 1
ai != bi
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 class Solution {
public:
    int vis[100001]={0};
    vector<pair<int,int>> adj[100001];
    
    int dfs(int i)
    {
        vis[i]=1;
        int ans=0;
        for(auto it: adj[i])
        {
            if(vis[it.first]==0)
            {
                ans+=it.second+dfs(it.first);
            }
        }
        return ans;
    }
    int minReorder(int n, vector<vector<int>>& con) {
        for(int i=0;i<con.size();i++)
        {
            adj[con[i][0]].push_back({con[i][1],0});
            adj[con[i][1]].push_back({con[i][0],1});
        }
        int ans=0;
        // for(int i=n-1;i>0;i--)
        // {
        //     if(vis[i]==0)
        //     {
                ans+=dfs(0);
        //     }
        // }
        return con.size()-ans;
    }
};
 </pre>

