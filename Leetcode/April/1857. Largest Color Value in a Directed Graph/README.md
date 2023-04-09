
<h2><a href="https://leetcode.com/problems/largest-color-value-in-a-directed-graph/description/">1857. Largest Color Value in a Directed Graph</a></h2>
<h3>Hard</h3>
<hr>
<div><p>
There is a directed graph of n colored nodes and m edges. The nodes are numbered from 0 to n - 1.

You are given a string colors where colors[i] is a lowercase English letter representing the color of the ith node in this graph (0-indexed). You are also given a 2D array edges where edges[j] = [aj, bj] indicates that there is a directed edge from node aj to node bj.

A valid path in the graph is a sequence of nodes x1 -> x2 -> x3 -> ... -> xk such that there is a directed edge from xi to xi+1 for every 1 <= i < k. The color value of the path is the number of nodes that are colored the most frequently occurring color along that path.

Return the largest color value of any valid path in the given graph, or -1 if the graph contains a cycle.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  colors = "abaca", edges = [[0,1],[0,2],[2,3],[3,4]]
<strong>Output:</strong> 3
</pre>
<pre>
Explanation:  The path 0 -> 2 -> 3 -> 4 contains 3 nodes that are colored "a" (red in the above image).
  </pre>
  

Constraints:
<pre>
n == colors.length
m == edges.length
1 <= n <= 105
0 <= m <= 105
colors consists of lowercase English letters.
0 <= aj, bj < n
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 // class Solution {
// public:
//    vector<int> TOPOSORT(int it,int n, vector<int> adj[],vector<int> &hastopo )
//    {
//        vector<int> indegree(n,0);
//         vector<int> ans;

//        for(int i=0;i<n;i++)
//        {
//            for(auto it: adj[i])
//            {
//                indegree[it]++;
//            }
//        }
//        queue<int> q;
//        for(int i=0;i<n;i++)
//        {
//            if(indegree[i]==0) q.push(i);
//        }
//        while(!q.empty())
//        {
//            int node=q.front(); q.pop();
//            ans.push_back(node);
//            hastopo[node]=1;
//            for(auto it: adj[node])
//            {
//               indegree[it]--;
//               if(indegree[it]==0) q.push(it);
//            }
//        }
//        return ans;
//    }


//    int dfs(int it, string color,vector<int> adj[],vector<int>& vis, vector<int>& has,vector<int> &hastopo )
//    {
//        vis[it]=1;
//        int x=color[it]-'a';
//        has[x]++;
//        cout<<"it = "<<it<<" "<<x<<"\n";
//       int ans=0;
//        for(auto i: adj[it])
//        {
//            if(vis[i]==0 && hastopo[i]==1)
//            {
//               ans=max(ans,dfs(i,color,adj,vis,has,hastopo));
//            }
//        }
//        x=0;
//        for(int i=0;i<26;i++) x=max(x,has[i]);
//        has[x]--;
//        return max(ans,x);
//    }
    


//     int largestPathValue(string colors, vector<vector<int>>& edges) {
//         int n=colors.size();
//         vector<int> adj[n];
//         for(int i=0;i<edges.size();i++)
//         {
//             adj[edges[i][0]].push_back(edges[i][1]);
//         }
//         vector<int> hastopo(n,0);
//         vector<int> topo=TOPOSORT(0,n, adj,hastopo);
//         if(topo.size()==0) return -1;
         
//         for(int i=0;i<topo.size();i++) cout<<topo[i]<<" ";  

//         vector<int> vis(n,0); 
//         int ans=0;
//         for(int i=0;i<topo.size();i++)
//         {
//             if(vis[i]==0)
//             {    
//                 vector<int> has(26,0);
//                 ans=max(ans, dfs(i,colors,adj,vis, has,hastopo));
//             }
//         }
//         return ans;
//     }
// };

class Solution {
public:
    int largestPathValue(string colors, vector<vector<int>>& edges) {
        int n = colors.size();
        int k = 26;
        vector<int> indegrees(n, 0);
        vector<vector<int>> graph(n, vector<int>());
        for (vector<int>& edge : edges) {
            int u = edge[0];
            int v = edge[1];
            graph[u].push_back(v);
            indegrees[v]++;
        }
        unordered_set<int> zero_indegree;
        for (int i = 0; i < n; i++) {
            if (indegrees[i] == 0) {
                zero_indegree.insert(i);
            }
        }
        vector<vector<int>> counts(n, vector<int>(k, 0));
        for (int i = 0; i < n; i++) {
            counts[i][colors[i] - 'a']++;
        }
        int max_count = 0;
        int visited = 0;
        while (!zero_indegree.empty()) {
            int u = *zero_indegree.begin();
            zero_indegree.erase(u);
            visited++;
            for (int v : graph[u]) {
                for (int i = 0; i < k; i++) {
                    counts[v][i] = max(counts[v][i], counts[u][i] + (colors[v] - 'a' == i ? 1 : 0));
                }
                indegrees[v]--;
                if (indegrees[v] == 0) {
                    zero_indegree.insert(v);
                }
            }
            max_count = max(max_count, *max_element(counts[u].begin(), counts[u].end()));
        }
        return visited == n ? max_count : -1;
    }
};
 </pre>

