
<h2><a href="https://leetcode.com/problems/possible-bipartition/description/">886. Possible Bipartition</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
 We want to split a group of n people (labeled from 1 to n) into two groups of any size. Each person may dislike some other people, and they should not go into the same group.

Given the integer n and the array dislikes where dislikes[i] = [ai, bi] indicates that the person labeled ai does not like the person labeled bi, return true if it is possible to split everyone into two groups in this way.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  n = 4, dislikes = [[1,2],[1,3],[2,4]]
<strong>Output:</strong>  true
</pre>
<pre>
group1 [1,4] and group2 [2,3].
  </pre>
 
Input: n = 3, dislikes = [[1,2],[1,3],[2,3]]
Output: false
 

Constraints:
<pre>
1 <= n <= 2000
0 <= dislikes.length <= 104
dislikes[i].length == 2
1 <= dislikes[i][j] <= n
ai < bi
All the pairs of dislikes are unique.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
         // simply apply is graph bipartitie in each components of the graph
class Solution {
public:
    bool possibleBipartition(int n, vector<vector<int>>& d) {
        queue<int> q;
        vector<int> adj[n+1];
        for(int i=0;i<d.size();i++)
        {
            adj[d[i][0]].push_back(d[i][1]);
            adj[d[i][1]].push_back(d[i][0]);
        }
        int vis[n+1];
        memset(vis,-1,sizeof(vis));
        
        for(int i=1;i<=n;i++)
        {
            if(vis[i]==-1)
        {q.push(i);
        vis[1]=0;}
        while(!q.empty())
        {
            int i=q.front(); q.pop();
            for(auto it : adj[i])
            {
                if(vis[it]==-1)
                {
                    vis[it]=1-vis[i];
                    q.push(it);
                }
                else if(vis[i]==vis[it])
                    return 0;
            }
        }
        }
        return 1;
        
    }
};
          
 </pre>

