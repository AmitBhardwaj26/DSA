
<h2><a href="https://leetcode.com/problems/count-unreachable-pairs-of-nodes-in-an-undirected-graph/description/">2316. Count Unreachable Pairs of Nodes in an Undirected Graph</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
 You are given an integer n. There is an undirected graph with n nodes, numbered from 0 to n - 1. You are given a 2D integer array edges where edges[i] = [ai, bi] denotes that there exists an undirected edge connecting nodes ai and bi.

Return the number of pairs of different nodes that are unreachable from each other.

 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>    n = 3, edges = [[0,1],[0,2],[1,2]]
<strong>Output:</strong> 0
</pre>
<pre>
Explanation: There are no pairs of nodes that are unreachable from each other. Therefore, we return 0.
  </pre>
  
Example 2:

Input: nums = [1], queries = [[4,0]]
Output: [0]
 

Constraints:
<pre>
1 <= n <= 105
0 <= edges.length <= 2 * 105
edges[i].length == 2
0 <= ai, bi < n
ai != bi
There are no repeated edges.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 class Solution {
public:
   
    int dfs(int i, vector<int> adj[], vector<int>& vis)
    {
        vis[i]=1;
        int ans=1;
        for(auto it: adj[i])
        {
           if(vis[it]==0)
           {
               vis[it]=1;
               ans+=dfs(it,adj,vis);
           }
        }
        return ans;
    }

    long long countPairs(int n, vector<vector<int>>& edges) {
        vector<long long> temp; long long ans=0;
        vector<int> adj[n+1];
        vector<int> vis(n+1,0);
        for(int i=0;i<edges.size();i++)
        {
            adj[edges[i][0]].push_back(edges[i][1]);
            adj[edges[i][1]].push_back(edges[i][0]);
        }
        for(int i=0;i<n;i++)
        { 
            if(vis[i]==0)
            {
             long long x=dfs(i,adj,vis);
              temp.push_back(x); 
              cout<<i<<" "<<x<<"\n";
            }
        }

        sort(temp.begin(),temp.end());
        vector<long long > t1(temp.begin(),temp.end());
       // for(int i=0;i<temp.size();i++) cout<<temp[i]<<" ";
        //cout<<endl;

        long long sum=0;
        for(int i=temp.size()-1; i>=0;i--)
        {
            sum+=temp[i];
            temp[i]=sum;
        }
        // for(int i=0;i<temp.size();i++) cout<<temp[i]<<" ";

        for(int i=0;i<temp.size()-1;i++)
        {
            ans+=t1[i]*temp[i+1];
        }

        return ans;
    }
};
 </pre>

