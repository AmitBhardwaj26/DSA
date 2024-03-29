
<h2><a href="https://leetcode.com/problems/minimum-score-of-a-path-between-two-cities/description/"></a></h2>2492. Minimum Score of a Path Between Two Cities
<h3>Medium</h3>
<hr>
<div><p>
You are given a positive integer n representing n cities numbered from 1 to n. You are also given a 2D array roads where roads[i] = [ai, bi, distancei] indicates that there is a bidirectional road between cities ai and bi with a distance equal to distancei. The cities graph is not necessarily connected.

The score of a path between two cities is defined as the minimum distance of a road in this path.

Return the minimum possible score of a path between cities 1 and n.

Note:

A path is a sequence of roads between two cities.
It is allowed for a path to contain the same road multiple times, and you can visit cities 1 and n multiple times along the path.
The test cases are generated such that there is at least one path between 1 and n.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   n = 4, roads = [[1,2,9],[2,3,6],[2,4,5],[1,4,7]]
<strong>Output:</strong> [8,6,2,4]
</pre>
<pre>
Explanation: The path from city 1 to 4 with the minimum score is: 1 -> 2 -> 4. The score of this path is min(9,5) = 5.
It can be shown that no other path has less score.
  </pre>


Constraints:
<pre>
2 <= n <= 105
1 <= roads.length <= 105
roads[i].length == 3
1 <= ai, bi <= n
ai != bi
1 <= distancei <= 104
There are no repeated edges.
There is at least one path between 1 and n.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 class Solution {
public:
    int minScore(int n, vector<vector<int>>& r) {
       // int n=r.size();
        vector<pair<int,int>> adj[n+1];
       for(int i=0;i<r.size();i++)
       {
           adj[r[i][0]].push_back({r[i][1],r[i][2]});
           adj[r[i][1]].push_back({r[i][0],r[i][2]});
       }
        int ans=INT_MAX;
	vector<int> vis(n+1, 0); vis[0] = 1;
	queue<int> q; q.push(1);
	while (!q.empty()) 
	{
		int node = q.front(); q.pop();
		// ans=min(ans,adj[node].second);
		for (auto it: adj[node])
		{
            ans=min(ans,it.second);
			if (!vis[it.first]) { 
                                  q.push(it.first); vis[it.first] = 1; } 
		}
	}
	    return ans;
    }
};
 </pre>

