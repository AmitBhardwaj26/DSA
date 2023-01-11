
<h2><a href="https://leetcode.com/problems/minimum-time-to-collect-all-apples-in-a-tree/description/">1443. Minimum Time to Collect All Apples in a Tree</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given an undirected tree consisting of n vertices numbered from 0 to n-1, which has some apples in their vertices. You spend 1 second to walk over one edge of the tree. Return the minimum time in seconds you have to spend to collect all apples in the tree, starting at vertex 0 and coming back to this vertex.

The edges of the undirected tree are given in the array edges, where edges[i] = [ai, bi] means that exists an edge connecting the vertices ai and bi. Additionally, there is a boolean array hasApple, where hasApple[i] = true means that vertex i has an apple; otherwise, it does not have any apple.

 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   n = 7, edges = [[0,1],[0,2],[1,4],[1,5],[2,3],[2,6]], hasApple = [false,false,true,false,true,true,false]
<strong>Output:</strong> 8 
</pre>
<pre>
Explanation:The figure above represents the given tree where red vertices have an apple. One optimal path to collect all apples is shown by the green arrows.  
  </pre>

 

Constraints:
<pre>
1 <= n <= 105
edges.length == n - 1
edges[i].length == 2
0 <= ai < bi <= n - 1
fromi < toi
hasApple.length == n
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
    class Solution {
      public:
          vector<vector<int>> adjList;
          int dfs(vector<bool>& hasApple,int node,int d,int prev)
          {
              int result=0,temp;
              for(int &i:adjList[node])
           if(i!=prev)
           {
               temp=dfs(hasApple,i,d+1,node);
               if(temp) result+=temp-d;
           }
              return result||hasApple[node]?result+d:0; 

          }
          int minTime(int n, vector<vector<int>>& edges, vector<bool>& hasApple) 
          {
              adjList.resize(n);
              for(vector<int> &e:edges)
                  adjList[e[0]].push_back(e[1]),adjList[e[1]].push_back(e[0]);
              return dfs(hasApple,0,0,-1)*2;
          }
      };
          
 </pre>

