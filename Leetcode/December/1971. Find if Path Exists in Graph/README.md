
<h2><a href="https://leetcode.com/problems/find-if-path-exists-in-graph/description/">1971. Find if Path Exists in Graph</a></h2>
<h3>Easy</h3>
<hr>
<div><p>
There is a bi-directional graph with n vertices, where each vertex is labeled from 0 to n - 1 (inclusive). The edges in the graph are represented as a 2D integer array edges, where each edges[i] = [ui, vi] denotes a bi-directional edge between vertex ui and vertex vi. Every vertex pair is connected by at most one edge, and no vertex has an edge to itself.

You want to determine if there is a valid path that exists from vertex source to vertex destination.

Given edges and the integers n, source, and destination, return true if there is a valid path from source to destination, or false otherwise.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   n = 3, edges = [[0,1],[1,2],[2,0]], source = 0, destination = 2
<strong>Output:</strong> true
</pre>
<pre>
There are two paths from vertex 0 to vertex 2:
- 0 → 1 → 2
- 0 → 2
  </pre>
  


Constraints:
<pre>
1 <= n <= 2 * 105
0 <= edges.length <= 2 * 105
edges[i].length == 2
0 <= ui, vi <= n - 1
ui != vi
0 <= source, destination <= n - 1
There are no duplicate edges.
There are no self edges.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
       class Solution {
public:
   
    bool validPath(int n, vector<vector<int>>& e, int source, int des) {
        vector<int> adj[n+1];
        for(int i=0;i<e.size();i++)
        {
            adj[e[i][0]].push_back(e[i][1]);
            adj[e[i][1]].push_back(e[i][0]);    
        }
        queue<int> q;
        q.push(source);
        vector<int> vis(n+1,0);
        while(q.size()>0)
        {
            int node =q.front(); q.pop(); 
            if(node==des) return 1;
            vis[node]=1;
            for(auto it: adj[node])
            {
                if( vis[it] ==0) q.push(it);
            }
        }
        return 0;
    }
};
          
 </pre>

