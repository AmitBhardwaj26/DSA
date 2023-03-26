
<h2><a href="https://leetcode.com/problems/longest-cycle-in-a-graph/description/">2360. Longest Cycle in a Graph</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
You are given a directed graph of n nodes numbered from 0 to n - 1, where each node has at most one outgoing edge.

The graph is represented with a given 0-indexed array edges of size n, indicating that there is a directed edge from node i to node edges[i]. If there is no outgoing edge from node i, then edges[i] == -1.

Return the length of the longest cycle in the graph. If no cycle exists, return -1.

A cycle is a path that starts and ends at the same node.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   edges = [3,3,4,2,3]
<strong>Output:</strong> 3
</pre>
<pre>
Explanation:The longest cycle in the graph is the cycle: 2 -> 4 -> 3 -> 2.
The length of this cycle is 3, so 3 is returned.
  </pre>
  


Constraints:
<pre>
n == edges.length
2 <= n <= 105
-1 <= edges[i] < n
edges[i] != i
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 class Solution {
public:
   // intution is simple 
   // step 1: find toposort it remove the edges which is a part of cycle
   // step 2: in any node do dfs call to find cycle 
    
    vector<int> Toposort(vector<int> &ed)
    {
        int n=ed.size();
        vector<int> ans(n,0),indegree(n,0);
        for(int i=0;i<n;i++)
          if(ed[i]>=0)  indegree[ed[i]]++;
         
        queue<int> q;   
        for(int i=0;i<n;i++)
        {
            if(indegree[i]==0 ) q.push(i);
        }
        while(!q.empty())
        {
            int x=q.front(); q.pop();
            ans[x]=1;
            if(ed[x]>=0) indegree[ed[x]]--;
            if(ed[x]>=0 &&indegree[ed[x]]==0) q.push(ed[x]);
        }
        return ans;
    }

    int dfs(int it,vector<int> &ed , vector<int> &vis, vector<int> &dis )
    {
        // cout<<it<<" ";
        vis[it]=1;
        dis[it]=1;
        int x=ed[it];
        if(dis[x]==1 && vis[x]==1) return 1;
        if(vis[x]==0)
        {
            return 1+dfs(x,ed,vis,dis);
        } 
        dis[it]=0;
        return 1;
    }
    
    int longestCycle(vector<int>& ed) {
        // apply toposoprth
        vector<int> vis= Toposort(ed);
        int n=ed.size(),ans=0;
        //for(int i=0;i<n;i++) cout<<vis[i]<<" ";
        //cout<<endl;
        
        vector<int> dis(n,0);
        for(int i=0;i<n;i++)
        {
           if(vis[i]==0 && ed[i]>=0) ans=max(ans,dfs(i,ed,vis,dis));
        }
        if(ans==0) return -1;
        return ans;                                                     
    }
};
 </pre>

