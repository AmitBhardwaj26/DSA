
<h2><a href="https://leetcode.com/problems/removing-stars-from-a-string/description/">2390. Removing Stars From a String</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
 [You are given an integer array nums and an array queries where queries[i] = [vali, indexi].

For each query i, first, apply nums[indexi] = nums[indexi] + vali, then print the sum of the even values of nums.

Return an integer array answer where answer[i] is the answer to the ith quer](https://leetcode.com/problems/removing-stars-from-a-string/description/)y.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  s = "leet**cod*e"
<strong>Output:</strong>  "lecoe"
</pre>
<pre>
Explanation: Performing the removals from left to right:
- The closest character to the 1st star is 't' in "leet**cod*e". s becomes "lee*cod*e".
- The closest character to the 2nd star is 'e' in "lee*cod*e". s becomes "lecod*e".
- The closest character to the 3rd star is 'd' in "lecod*e". s becomes "lecoe".
There are no more stars, so we return "lecoe".
  </pre>
  
 

Constraints:
<pre>
1 <= s.length <= 105
s consists of lowercase English letters and stars *.
The operation above can be performed on s.

</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
class Solution {
public:
    string removeStars(string s) {
        stack<int> st;
        for(int i=0;i<s.size();i++)
        {
            if(s[i]=='*') st.pop();
            else st.push(s[i]);
            
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

