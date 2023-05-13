
<h2><a href="https://leetcode.com/problems/lexicographically-smallest-equivalent-string/description/">1061. Lexicographically Smallest Equivalent String</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
You are given two strings of the same length s1 and s2 and a string baseStr.

We say s1[i] and s2[i] are equivalent characters.

For example, if s1 = "abc" and s2 = "cde", then we have 'a' == 'c', 'b' == 'd', and 'c' == 'e'.
Equivalent characters follow the usual rules of any equivalence relation:

Reflexivity: 'a' == 'a'.
Symmetry: 'a' == 'b' implies 'b' == 'a'.
Transitivity: 'a' == 'b' and 'b' == 'c' implies 'a' == 'c'.
For example, given the equivalency information from s1 = "abc" and s2 = "cde", "acd" and "aab" are equivalent strings of baseStr = "eed", and "aab" is the lexicographically smallest equivalent string of baseStr.

Return the lexicographically smallest equivalent string of baseStr by using the equivalency information from s1 and s2.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   s1 = "parker", s2 = "morris", baseStr = "parser"
<strong>Output:</strong>  "makkek"
</pre>
<pre>
 Based on the equivalency information in s1 and s2, we can group their characters as [m,p], [a,o], [k,r,s], [e,i].
The characters in each group are equivalent and sorted in lexicographical order.
So the answer is "makkek".
  </pre>
 
Constraints:
<pre>
1 <= nums.length <= 104
-104 <= nums[i] <= 104
1 <= queries.length <= 104
-104 <= vali <= 104
0 <= indexi < nums.length
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
   class Solution {
      public:
          int par[26];

          int find(int x){
              if(par[x]==-1) return x;
              return par[x]=find(par[x]);
          }

          void Union(int x, int y) {
              x = find(x);
              y = find(y);

              if (x != y) 
                  par[max(x, y)] = min(x, y); 
          }

          string smallestEquivalentString(string s1, string s2, string baseStr) {

              memset(par, -1, sizeof(par));

              for (auto i = 0; i < s1.size(); ++i) 
                  Union(s1[i] - 'a', s2[i] - 'a');

              for(auto i=0;i<baseStr.size();i++) 
                  baseStr[i]=find(baseStr[i]-'a')+'a';

              return baseStr;
          }
      };
          
 </pre>

