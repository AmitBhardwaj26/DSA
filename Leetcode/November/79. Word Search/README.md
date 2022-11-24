
<h2><a href="https://leetcode.com/problems/word-search/description/">79. Word Search</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given an m x n grid of characters board and a string word, return true if word exists in the grid.

The word can be constructed from letters of sequentially adjacent cells, where adjacent cells are horizontally or vertically neighboring. The same letter cell may not be used more than once.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   board = [["A","B","C","E"],["S","F","C","S"],["A","D","E","E"]], word = "ABCCED"
<strong>Output:</strong> true
</pre>


Constraints:
<pre>
m == board.length
n = board[i].length
1 <= m, n <= 6
1 <= word.length <= 15
board and word consists of only lowercase and uppercase English letters.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
      class Solution {
public:
    int dir[4][2]={{-1,0},{0,-1},{0,1},{1,0}};
    int n,m;
    bool solve(int x,int y,vector<vector<char>> &v,int p, string w  )
    {
        //cout<<x<<" "<<y<<endl;
        if(p==w.size()) return 1;
        if(x>=n || y>=m || x<0 || y<0 || w[p]!=v[x][y]) return 0;
        
        char temp=v[x][y];
        v[x][y]=' ';
        bool check=false;
        for(int i=0;i<4;i++)
        {
           int X= x+dir[i][0],Y=y+dir[i][1];
           //cout<<X<<" "<<Y<<endl;
          check|=solve(X,Y,v,p+1,w);
        }
        v[x][y]=temp;
        return check;
    } 

    bool exist(vector<vector<char>>& b, string w) {
      n=b.size(),m=b[0].size();
      for(int i=0;i<n;i++)
      {
          for(int j=0;j<m;j++)
          {
              if(b[i][j]==w[0] and solve(i,j,b,0,w)) return 1;
          }
      }
      return 0;    
    }
};
          
 </pre>


