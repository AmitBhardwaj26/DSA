
<h2><a href="https://leetcode.com/problems/valid-sudoku/description/">36. Valid Sudoku</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
 Determine if a 9 x 9 Sudoku board is valid. Only the filled cells need to be validated according to the following rules:

Each row must contain the digits 1-9 without repetition.
Each column must contain the digits 1-9 without repetition.
Each of the nine 3 x 3 sub-boxes of the grid must contain the digits 1-9 without repetition.
Note:

A Sudoku board (partially filled) could be valid but is not necessarily solvable.
Only the filled cells need to be validated according to the mentioned rules.
 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> board = 
[["5","3",".",".","7",".",".",".","."]
,["6",".",".","1","9","5",".",".","."]
,[".","9","8",".",".",".",".","6","."]
,["8",".",".",".","6",".",".",".","3"]
,["4",".",".","8",".","3",".",".","1"]
,["7",".",".",".","2",".",".",".","6"]
,[".","6",".",".",".",".","2","8","."]
,[".",".",".","4","1","9",".",".","5"]
,[".",".",".",".","8",".",".","7","9"]]
<strong>Output:</strong> true
</pre>

  

 

Constraints:
<pre>
board.length == 9
board[i].length == 9
board[i][j] is a digit 1-9 or '.'.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
 class Solution {
   public:

       bool small(vector<vector<char>>& b,int x,int y)
   {
        int start_i=(x/3)*3;   
        int start_j=(y/3)*3;

        int val=b[x][y];
        for(int i=start_i;i<start_i+3;i++)
        {
                for(int j=start_j;j<start_j+3;j++)
                {
                        if(val==b[i][j] and (x!=i || j!=y))
                                return false;
                }
        }
        return true;
   }
       bool isValidSudoku(vector<vector<char>>& b) {
           int n=b.size(); bool check=true;
           for(int i=0;i<n;i++) 
           {   int a[100]={0},c[100]={0};
               for(int j=0;j<n;j++)
               {
                   if(b[i][j]!=',' && b[i][j]!='.')
                   {

                      // cout<<a[b[i][j]]<<" "<<b[i][j]<<" ";
                       if(a[b[i][j]]==1) {check=false; break;}
                       else a[b[i][j]]=1;
                   }
                       if(b[j][i]!=',' && b[j][i]!='.')
                   {
                       if(c[b[j][i]]==1) {check=false; break;}
                       else c[b[j][i]]=1;
                   }
               }
           }

            for(int i=0;i<9;i++)
       {
               for(int j=0;j<9;j++)
               {
                       if(b[i][j]!='.')
                       if(!small(b,i,j) )
                       {
                               return false;
                       }
               }
       }

           if(check) return true; 
           else return false;
       }
   };
          
 </pre>

