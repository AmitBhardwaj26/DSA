
<h2><a href="https://leetcode.com/problems/most-stones-removed-with-same-row-or-column/description/">947. Most Stones Removed with Same Row or Column</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
On a 2D plane, we place n stones at some integer coordinate points. Each coordinate point may have at most one stone.

A stone can be removed if it shares either the same row or the same column as another stone that has not been removed.

Given an array stones of length n where stones[i] = [xi, yi] represents the location of the ith stone, return the largest possible number of stones that can be removed.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>    stones = [[0,0],[0,1],[1,0],[1,2],[2,1],[2,2]]
<strong>Output:</strong> 5
</pre>
<pre>
One way to remove 5 stones is as follows:
1. Remove stone [2,2] because it shares the same row as [2,1].
2. Remove stone [2,1] because it shares the same column as [0,1].
3. Remove stone [1,2] because it shares the same row as [1,0].
4. Remove stone [1,0] because it shares the same column as [0,0].
5. Remove stone [0,1] because it shares the same row as [0,0].
Stone [0,0] cannot be removed since it does not share a row/column with another stone still on the plane.
  </pre>
  


Constraints:
<pre>
1 <= stones.length <= 1000
0 <= xi, yi <= 104
No two stones are at the same coordinate point.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 class Solution {
public:
    int n;
    void dfs(int j,vector<int> &vis,vector<vector<int>>& s )
    {
       if(j==n) return ;
       vis[j]=1;
       
       for(int i=0;i<n;i++)
       {
          if(vis[i]==0 && (s[i][0]==s[j][0] || s[i][1]==s[j][1]))
          {
            dfs(i,vis,s);
          } 
       }
       return ;
    }
    int removeStones(vector<vector<int>>& s) {
        int count=0; n=s.size();
        vector<int> vis(n,0);
        for(int i=0;i<n;i++)
        {
            if(vis[i]==0) 
            {
                dfs(i,vis,s);
              count++;
            }
        }
        return n-count;
    }
};
          
 </pre>

