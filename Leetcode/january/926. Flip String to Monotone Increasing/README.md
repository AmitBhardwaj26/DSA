
<h2><a href="https://leetcode.com/problems/flip-string-to-monotone-increasing/description/">926. Flip String to Monotone Increasing</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
A binary string is monotone increasing if it consists of some number of 0's (possibly none), followed by some number of 1's (also possibly none).

You are given a binary string s. You can flip s[i] changing it from 0 to 1 or from 1 to 0.

Return the minimum number of flips to make s monotone increasing.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  s = "00110"
<strong>Output:</strong> 1
</pre>
<pre>
Explanation: We flip the last digit to get 00111.
  </pre>
  

Constraints:
<pre>
1 <= s.length <= 105
s[i] is either '0' or '1'.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
        class Solution {
public:
    int minFlipsMonoIncr(string s) {
        int ans=INT_MAX,x0=0,y0=0;
        for(int i=s.size()-1;i>=0;i--) if(s[i]=='0') y0++;
        for(int i=0;i<s.size();i++)
        {
            ans=min(ans,y0+x0);
            if(s[i]=='0') y0--;
            else x0++;
        }
          ans=min(ans,y0+x0);
          return ans;
    }
};
          
 </pre>

