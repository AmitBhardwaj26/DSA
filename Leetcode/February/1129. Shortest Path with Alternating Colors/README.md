
<h2><a href="https://leetcode.com/problems/sum-of-even-numbers-after-queries/">985. Sum of Even Numbers After Queries</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
You are given an integer n, the number of nodes in a directed graph where the nodes are labeled from 0 to n - 1. Each edge is red or blue in this graph, and there could be self-edges and parallel edges.

You are given two arrays redEdges and blueEdges where:

redEdges[i] = [ai, bi] indicates that there is a directed red edge from node ai to node bi in the graph, and
blueEdges[j] = [uj, vj] indicates that there is a directed blue edge from node uj to node vj in the graph.
Return an array answer of length n, where each answer[x] is the length of the shortest path from node 0 to node x such that the edge colors alternate along the path, or -1 if such a path does not exist.

 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> n = 3, redEdges = [[0,1],[1,2]], blueEdges = []
<strong>Output:</strong> [0,1,-1]
</pre>

 

Constraints:
<pre>
1 <= n <= 100
0 <= redEdges.length, blueEdges.length <= 400
redEdges[i].length == blueEdges[j].length == 2
0 <= ai, bi, uj, vj < n
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 class Solution {
public:
  vector<int> shortestAlternatingPaths(int n, vector<vector<int>>& redEdges, vector<vector<int>>& blueEdges) {
        vector<int>ans(n,-1);
        queue<vector<int>>q;
        vector<pair<int,int>>adj[n];
        for(auto it:redEdges){
            adj[it[0]].push_back({it[1],0});
        }
        for(auto it:blueEdges){
            adj[it[0]].push_back({it[1],1});
        }
        ans[0]=0;
        q.push({0,0,-1}); // node, dist,color
        while(!q.empty()){
            vector<int>temp=q.front();
            int node=temp[0];
            int prev=temp[2];
            q.pop();
           if(ans[node]==-1) ans[node]=temp[1];
            for(auto &x:adj[node]){
                // Most Important step to put & while editing in the loop
                if(x.second!=prev && x.first!=-1){
                    q.push({x.first,temp[1]+1,x.second});
                    x.first=-1;
                }
            }
        }
       
        return ans;
    }
};
          
 </pre>

