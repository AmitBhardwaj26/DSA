
<h2><a href="https://leetcode.com/problems/all-paths-from-source-to-target/description/">797.All Paths From Source to Target</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given a directed acyclic graph (DAG) of n nodes labeled from 0 to n - 1, find all possible paths from node 0 to node n - 1 and return them in any order.

The graph is given as follows: graph[i] is a list of all nodes you can visit from node i (i.e., there is a directed edge from node i to node graph[i][j]).
 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  graph = [[1,2],[3],[3],[]]
<strong>Output:</strong>[[0,1,3],[0,2,3]]
</pre>
<pre>
There are two paths: 0 -> 1 -> 3 and 0 -> 2 -> 3.
  </pre>


Constraints:
<pre>

n == graph.length
2 <= n <= 15
0 <= graph[i][j] < n
graph[i][j] != i (i.e., there will be no self-loops).
All the elements of graph[i] are unique.
The input graph is guaranteed to be a DAG.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
         class Solution {
public: vector<vector<int>> ans;
    void solve(vector<vector<int>> &adj, int i, vector<int> &vis,  vector<int> &v)
    {
        if(vis[i]==0)
        {
            vis[i]=1;
            v.push_back(i);
            if(i==adj.size()-1) ans.push_back(v);
            for(auto it: adj[i])
            {
                solve(adj,it,vis,v);
            }
            vis[i]=0;
            v.pop_back();
        }
        
    }
    
    vector<vector<int>> allPathsSourceTarget(vector<vector<int>>& graph) {
        // dfs
        vector<int> vis(graph.size()+1,0);
        vector<int> v;
        solve(graph,0,vis,v);
        return ans;
    }
};
          
 </pre>

