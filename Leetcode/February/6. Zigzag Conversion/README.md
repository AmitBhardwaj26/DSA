
<h2><a href="https://leetcode.com/problems/sum-of-even-numbers-after-queries/">6. Zigzag Conversion</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
 The string "PAYPALISHIRING" is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility)

P   A   H   N
A P L S I I G
Y   I   R
And then read line by line: "PAHNAPLSIIGYIR"

Write the code that will take a string and make this conversion given a number of rows:

string convert(string s, int numRows);
 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>    s = "PAYPALISHIRING", numRows = 3
<strong>Output:</strong> "PAHNAPLSIIGYIR"
</pre>

 

Constraints:
<pre>
1 <= s.length <= 1000
s consists of English letters (lower-case and upper-case), ',' and '.'.
1 <= numRows <= 1000
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 // create a string array of size n push into the string and change the direction of motion whenever required.

class Solution {
public:
    string convert(string s, int n) {
        if(n==1) return s;
        string v[n+1];
        int dir=1,ind=1;
        for(int i=0;i<s.size();i++)
        {
           v[ind]+=s[i];
           ind+=dir;
           if(ind==n) dir=-1;
           else if(ind==1) dir=1;
        }
        string ans="";
        for(int i=1;i<=n;i++) ans+=v[i];
        return ans;

    }
};
 </pre>

