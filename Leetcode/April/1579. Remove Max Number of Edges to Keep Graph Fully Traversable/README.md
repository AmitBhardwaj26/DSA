
<h2><a href="https://leetcode.com/problems/remove-max-number-of-edges-to-keep-graph-fully-traversable/description/">1579. Remove Max Number of Edges to Keep Graph Fully Traversable</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Alice and Bob have an undirected graph of n nodes and three types of edges:

Type 1: Can be traversed by Alice only.
Type 2: Can be traversed by Bob only.
Type 3: Can be traversed by both Alice and Bob.
Given an array edges where edges[i] = [typei, ui, vi] represents a bidirectional edge of type typei between nodes ui and vi, find the maximum number of edges you can remove so that after removing the edges, the graph can still be fully traversed by both Alice and Bob. The graph is fully traversed by Alice and Bob if starting from any node, they can reach all other nodes.

Return the maximum number of edges you can remove, or return -1 if Alice and Bob cannot fully traverse the graph.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>    n = 4, edges = [[3,1,2],[3,2,3],[1,1,3],[1,2,4],[1,1,2],[2,3,4]]
<strong>Output:</strong> 2
</pre>
<pre>
Explanation: If we remove the 2 edges [1,1,2] and [1,1,3]. The graph will still be fully traversable by Alice and Bob. Removing any additional edge will not make it so. So the maximum number of edges we can remove is 2.
  </pre>
  
Example 2:

Input: nums = [1], queries = [[4,0]]
Output: [0]
 

Constraints:
<pre>
1 <= n <= 105
1 <= edges.length <= min(105, 3 * n * (n - 1) / 2)
edges[i].length == 3
1 <= typei <= 3
1 <= ui < vi <= n
All tuples (typei, ui, vi) are distinct.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 class DisjointSet {
    vector<int> rank, parent, size;
public:
    DisjointSet(int n) {
        rank.resize(n + 1, 0);
        parent.resize(n + 1);
        size.resize(n + 1);
        for (int i = 0; i <= n; i++) {
            parent[i] = i;
            size[i] = 1;
        }
    }

    int findUPar(int node) {
        if (node == parent[node])
            return node;
        return parent[node] = findUPar(parent[node]);
    }

    void unionBySize(int u, int v) {
        int ulp_u = findUPar(u);
        int ulp_v = findUPar(v);
        if (ulp_u == ulp_v) return;
        if (size[ulp_u] < size[ulp_v]) {
            parent[ulp_u] = ulp_v;
            size[ulp_v] += size[ulp_u];
        }
        else {
            parent[ulp_v] = ulp_u;
            size[ulp_u] += size[ulp_v];
        }
    }
};


class Solution {
public:
    int maxNumEdgesToRemove(int n, vector<vector<int>>& edges) {
        DisjointSet ds1(n),ds2(n);
        int ans=0;
        //cout<<edges.size()<<" ";
        for(auto it: edges)
        {
            bool check1=0,check2=0;
            if(it[0]==3 )
            {
                if(ds1.findUPar(it[1])!=ds1.findUPar(it[2]))
                   ds1.unionBySize(it[1],it[2]); 
                else check1=1;

                if(ds2.findUPar(it[1])!=ds2.findUPar(it[2]))
                   ds2.unionBySize(it[1],it[2]);
                else check2=1;

                if(check1 && check2) ans++;
            }   
        }
        //cout<<ans<<"\n";
        for(auto it: edges)
        {
            if(it[0]==1 )
            {
                if(ds1.findUPar(it[1])!=ds1.findUPar(it[2]))
                   ds1.unionBySize(it[1],it[2]);
                else ans++;
            }
            else if(it[0]==2 )
            {
                if(ds2.findUPar(it[1])!=ds2.findUPar(it[2]))
                   ds2.unionBySize(it[1],it[2]);
                else ans++;
            } 
        }
        set<int> s1,s2;
        for(int i=1;i<=n;i++)
        {
            int x=ds1.findUPar(i),y=ds2.findUPar(i);
            if(x>0) s1.insert(x); 
            if(y>0) s2.insert(y);
            if(s1.size()>1 || s2.size()>1 ) return -1;
        }

        return ans;
    }
};
 </pre>


