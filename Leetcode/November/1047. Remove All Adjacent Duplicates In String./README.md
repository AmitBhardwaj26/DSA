
<h2><a href="https://leetcode.com/problems/remove-all-adjacent-duplicates-in-string/description/">1047. Remove All Adjacent Duplicates In String
</a></h2>
<h3>Easy</h3>
<hr>
<div><p>
 You are given a string S consisting of lowercase English letters. A duplicate removal consists of choosing two adjacent and equal letters and removing them.

We repeatedly make duplicate removals on s until we no longer can.

Return the final string after all such duplicate removals have been made. It can be proven that the answer is unique.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   s = "abbaca"
<strong>Output:</strong> "ca"
</pre>
<pre>
For example, in "abbaca" we could remove "bb" since the letters are adjacent and equal, and this is the only possible move.  The result of this move is that the string is "aaca", of which only "aa" is possible, so the final string is "ca".
  </pre>
  
Example 2:

Input: nums = [1], queries = [[4,0]]
Output: [0]
 

Constraints:
<pre>
1 <= s.length <= 105
s consists of lowercase English letters.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
      class Solution {
         public:
             string removeDuplicates(string s) {
                 stack<char> st;
                 for(int i=0;i<s.size();i++)
                 {
                      if(st.empty()) st.push(s[i]);
                      else 
                      {
                           if(st.top()==s[i]) st.pop();
                           else st.push(s[i]);
                      }
                 }
                 string ans="";
                 while(!st.empty())
                 {
                     ans+=st.top();
                     st.pop();
                 }
                 reverse(ans.begin(),ans.end());
                 return ans;
             }
};
          
 </pre>

