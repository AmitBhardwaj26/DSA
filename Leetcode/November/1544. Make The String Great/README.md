
<h2><a href="https://leetcode.com/problems/make-the-string-great/">1544. Make The String Great</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given a string s of lower and upper case English letters.

A good string is a string which doesn't have two adjacent characters s[i] and s[i + 1] where:

0 <= i <= s.length - 2
s[i] is a lower-case letter and s[i + 1] is the same letter but in upper-case or vice-versa.
To make the string good, you can choose two adjacent characters that make the string bad and remove them. You can keep doing this until the string becomes good.

Return the string after making it good. The answer is guaranteed to be unique under the given constraints.

Notice that an empty string is also good.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>    s = "leEeetcode"
<strong>Output:</strong> "leetcode"
</pre>
<pre>
In the first step, either you choose i = 1 or i = 2, both will result "leEeetcode" to be reduced to "leetcode".
  </pre>
  
Input: s = "abBAcC"
Output: ""
Explanation: We have many possible scenarios, and all lead to the same answer. For example:
"abBAcC" --> "aAcC" --> "cC" --> ""
"abBAcC" --> "abBA" --> "aA" --> ""
 

Constraints:
<pre>
1 <= s.length <= 100
s contains only lower and upper case English letters.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
          class Solution {
public:
    string makeGood(string s) {
        stack<char> st;
        for(int i=0;i<s.size();i++)
        {
             if(st.empty()) st.push(s[i]);
             else 
             {
                     char a=st.top(),b=s[i];
                     cout<<a<<" "<<b<<"\n";
                     if(a<='Z' && b>='a' && a-'A'==b-'a') st.pop();
                     else if(b<='Z' && a>='a' && (a-'a')==(b-'A') ) st.pop();
                     else st.push(s[i]);
             }
        }
        string ans="";
        while(!st.empty())
        {
             ans=st.top()+ans; st.pop();
        }
        return ans;
    }
};
          
 </pre>

