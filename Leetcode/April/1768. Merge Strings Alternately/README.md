
<h2><a href="https://leetcode.com/problems/merge-strings-alternately/description/">1768. Merge Strings Alternately</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
You are given two strings word1 and word2. Merge the strings by adding letters in alternating order, starting with word1. If a string is longer than the other, append the additional letters onto the end of the merged string.

Return the merged string.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>    word1 = "abc", word2 = "pqr"
<strong>Output:</strong> "apbqcr"
</pre>
<pre>
Explanation: The merged string will be merged as so:
word1:  a   b   c
word2:    p   q   r
merged: a p b q c r
  </pre>
 

Constraints:
<pre>
1 <= word1.length, word2.length <= 100
word1 and word2 consist of lowercase English letters.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 class Solution {
public:
    string mergeAlternately(string word1, string word2) {
        string ans="";
        int i=0,j=0;
        while(i<word1.size() && j<word2.size())
        {
            ans+=word1[i++];
            ans+=word2[j++];
        }
        while(i<word1.size()) ans+=word1[i++];
        while(j<word2.size()) ans+=word2[j++];
        return ans;
    }
};
 </pre>

