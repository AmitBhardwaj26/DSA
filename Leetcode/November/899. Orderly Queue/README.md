
<h2><a href="https://leetcode.com/problems/orderly-queue/">899. Orderly Queue</a></h2>
<h3>Hard</h3>
<hr>
<div><p>
You are given a string s and an integer k. You can choose one of the first k letters of s and append it at the end of the string..

Return the lexicographically smallest string you could have after applying the mentioned step any number of moves.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  s = "cba", k = 1
<strong>Output:</strong> "acb"
</pre>
<pre>
In the first move, we move the 1st character 'c' to the end, obtaining the string "bac".
In the second move, we move the 1st character 'b' to the end, obtaining the final result "acb".
  </pre>
  
Input: s = "baaca", k = 3
Output: "aaabc"
Explanation: 
In the first move, we move the 1st character 'b' to the end, obtaining the string "aacab".
In the second move, we move the 3rd character 'c' to the end, obtaining the final result "aaabc".

Constraints:
<pre>
1 <= k <= s.length <= 1000
s consist of lowercase English letters.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
         class Solution {
          public:
              string orderlyQueue(string s, int k) {
                 if(k==1)
                 {
                    string ans=s;
                    s+=s;
                    int x=ans.size();
                    for(int i=0;i<s.size()-x;i++)
                    {
                        ans=min(ans,s.substr(i,x));
                    }
                     return ans;
                 }   
                 else
                 {
                     sort(s.begin(),s.end());
                     return s; 
                 }
              }
          };
 </pre>

