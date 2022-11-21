
<h2><a href="https://leetcode.com/problems/nearest-exit-from-entrance-in-maze/">1926. Nearest Exit from Entrance in Maze</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
 You are given an m x n matrix maze (0-indexed) with empty cells (represented as '.') and walls (represented as '+'). You are also given the entrance of the maze, where entrance = [entrancerow, entrancecol] denotes the row and column of the cell you are initially standing at.

In one step, you can move one cell up, down, left, or right. You cannot step into a cell with a wall, and you cannot step outside the maze. Your goal is to find the nearest exit from the entrance. An exit is defined as an empty cell that is at the border of the maze. The entrance does not count as an exit.

Return the number of steps in the shortest path from the entrance to the nearest exit, or -1 if no such path exists.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   maze = [["+","+",".","+"],[".",".",".","+"],["+","+","+","."]], entrance = [1,2]
<strong>Output:</strong> 1
</pre>
<pre>
There are 3 exits in this maze at [1,0], [0,2], and [2,3].
Initially, you are at the entrance cell [1,2].
- You can reach [1,0] by moving 2 steps left.
- You can reach [0,2] by moving 1 step up.
It is impossible to reach [2,3] from the entrance.
Thus, the nearest exit is [0,2], which is 1 step away.
  </pre>
  

Constraints:
<pre>
maze.length == m
maze[i].length == n
1 <= m, n <= 100
maze[i][j] is either '.' or '+'.
entrance.length == 2
0 <= entrancerow < m
0 <= entrancecol < n
entrance will always be an empty cell.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
        //never use dfs to find shortest distence its mith use always bfs
class Solution {
public:
    int nearestExit(vector<vector<char>>& maze, vector<int>& entrance) {
        int rows = maze.size();
        int cols = maze[0].size();
        if(maze[entrance[0]][entrance[1]]=='+')
            return -1;
        queue<pair<int,int>>q;
        q.push({entrance[0],entrance[1]});
        maze[entrance[0]][entrance[1]]='+';
        int dist = -1;
        while(!q.empty()){
            dist++;
            int size = q.size();
            for(int i=0;i<size;i++){
                auto node = q.front();q.pop();
                
                int x = node.first;
                int y = node.second;
                
                if(((x==rows-1 or x==0) or (y==0 or y==cols-1)) and dist!=0)
                    return dist;
                
                if(x+1<rows and maze[x+1][y]!='+'){
                    maze[x+1][y]='+';
                    q.push({x+1,y});
                }
                if(y+1<cols and maze[x][y+1]!='+'){
                    maze[x][y+1]='+';
                    q.push({x,y+1});
                }
                if(x-1>=0 and maze[x-1][y]!='+'){
                    maze[x-1][y]='+';
                    q.push({x-1,y});
                }
                if(y-1>=0 and maze[x][y-1]!='+'){
                    maze[x][y-1]='+';
                    q.push({x,y-1});
                }
            }
        }
        return -1;
    }
};
          
 </pre>

