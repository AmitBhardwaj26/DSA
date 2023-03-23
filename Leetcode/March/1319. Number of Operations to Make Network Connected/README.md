
<h2><a href="https://leetcode.com/problems/number-of-operations-to-make-network-connected/description/">1319. Number of Operations to Make Network Connected</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
There are n computers numbered from 0 to n - 1 connected by ethernet cables connections forming a network where connections[i] = [ai, bi] represents a connection between computers ai and bi. Any computer can reach any other computer directly or indirectly through the network.

You are given an initial computer network connections. You can extract certain cables between two directly connected computers, and place them between any pair of disconnected computers to make them directly connected.

Return the minimum number of times you need to do this in order to make all the computers connected. If it is not possible, return -1.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   n = 4, connections = [[0,1],[0,2],[1,2]]
<strong>Output:</strong> 1
</pre>
<pre>
Explanation:Remove cable between computer 1 and 2 and place between computers 1 and 3.
  </pre>


Constraints:
<pre>
1 <= n <= 105
1 <= connections.length <= min(n * (n - 1) / 2, 105)
connections[i].length == 2
0 <= ai, bi < n
ai != bi
There are no repeated connections.
No two computers are connected by more than one cable.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 // simple DFS anf find the total number of disconneted components by making count in for loop

class Solution {
public:
    int vis[100001]={0};
    vector<int> adj[100001];
    void dfs(int i)
    {
        vis[i]=1;
        for(auto it: adj[i])
        {
            if(vis[it]==0)  dfs(it);
        }
        return ;
    }
    
    int makeConnected(int n, vector<vector<int>>& con) {
        // vector<int> adj[n]; N=n;
        for(int i=0;i<con.size();i++)
        {
            adj[con[i][0]].push_back(con[i][1]);
            adj[con[i][1]].push_back(con[i][0]);   
        }
        int ans=0;
        for(int i=0;i<n;i++)
        {
            if(vis[i]==0) 
            {
                dfs(i);
                // cout<<i<<" ";
                ans++;
            }
        }
        
        if(n-1>con.size()) return -1;
        return ans-1;
    }
};
 </pre>

