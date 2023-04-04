
<h2><a href="https://leetcode.com/problems/sum-of-even-numbers-after-queries/">985. Sum of Even Numbers After Queries</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given a string s, partition the string into one or more substrings such that the characters in each substring are unique. That is, no letter appears in a single substring more than once.

Return the minimum number of substrings in such a partition.

Note that each character should belong to exactly one substring in a partition.

 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   s = "abacaba"
<strong>Output:</strong> 4
</pre>
<pre>
Explanation: Two possible partitions are ("a","ba","cab","a") and ("ab","a","ca","ba").
It can be shown that 4 is the minimum number of substrings needed.
  </pre>

 

Constraints:
<pre>
1 <= s.length <= 105
s consists of only English lowercase letters.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
class Solution {
public:
    int partitionString(string s) {
        int a[26]={0},ans=1;
        
        for(int i=0;i<s.size();i++)
        { 
            int x=s[i]-'a';
            if(a[x]>0) 
            {
                for(int i=0;i<26;i++) a[i]=0;
                a[x]=1;
                ans++;
            } 
            else a[x]++;
        }
        return ans;
    }
};
 </pre>

