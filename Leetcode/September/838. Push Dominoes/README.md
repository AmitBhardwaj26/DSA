
<h2><a href="https://leetcode.com/problems/push-dominoes/">838. Push Dominoes</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
There are n dominoes in a line, and we place each domino vertically upright. In the beginning, we simultaneously push some of the dominoes either to the left or to the right.

After each second, each domino that is falling to the left pushes the adjacent domino on the left. Similarly, the dominoes falling to the right push their adjacent dominoes standing on the right.

When a vertical domino has dominoes falling on it from both sides, it stays still due to the balance of the forces.

For the purposes of this question, we will consider that a falling domino expends no additional force to a falling or already fallen domino.

You are given a string dominoes representing the initial state where:

dominoes[i] = 'L', if the ith domino has been pushed to the left,
dominoes[i] = 'R', if the ith domino has been pushed to the right, and
dominoes[i] = '.', if the ith domino has not been pushed.
Return a string representing the final state.  
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  dominoes = "RR.L"
<strong>Output:</strong> "RR.L"
</pre>
 
  <p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  dominoes = ".L.R...LR..L.."
<strong>Output:</strong> "LL.RR.LLRRLL.."
</pre>
 

Constraints:
<pre>
n == dominoes.length
1 <= n <= 105
dominoes[i] is either 'L', 'R', or '.'.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 class Solution {
public:
    string pushDominoes(string d) {
        int n=d.size();
        vector<int> v(n,0); string s=d;
        int r=-1,l=-1;
        for(int i=0;i<n;i++)
        {
            if(d[i]=='R') {r=0;}
            else if(d[i]=='L') r=-1;
            if(r>=0) {v[i]=r; r++; s[i]='R';}
            // cout<<s[i]<<" "<<v[i]<<"\n";
        }
        // cout<<"|"<<endl;
        for(int i=n-1;i>=0;i--)
        {
            if(d[i]=='L') {l=0;}
            else if(d[i]=='R') l=-1;
             if(l>=0 )
            {
                if(v[i]>l || s[i]=='.') {s[i]='L'; v[i]=l; }
                else if(v[i]==l && l!=0) { s[i]='.'; }
                l++;
            }
            // cout<<s[i]<<" "<<v[i]<<"\n";
        }
        return s;
        
    }
};
          
 </pre>

