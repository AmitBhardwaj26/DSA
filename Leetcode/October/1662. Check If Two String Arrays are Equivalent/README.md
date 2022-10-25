
<h2><a href="https://leetcode.com/problems/check-if-two-string-arrays-are-equivalent/description/">1662. Check If Two String Arrays are Equivalent</a></h2>
<h3>Easy</h3>
<hr>
<div><p>
Given two string arrays word1 and word2, return true if the two arrays represent the same string, and false otherwise.

A string is represented by an array if the array elements concatenated in order forms the string.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  word1 = ["ab", "c"], word2 = ["a", "bc"]
<strong>Output:</strong> true
</pre>
<pre>
word1 represents string "ab" + "c" -> "abc"
word2 represents string "a" + "bc" -> "abc"
The strings are the same, so return true.
  </pre>
  
Example 2:

Input: word1 = ["a", "cb"], word2 = ["ab", "c"]
Output: false

Constraints:
<pre>
1 <= word1.length, word2.length <= 103
1 <= word1[i].length, word2[i].length <= 103
1 <= sum(word1[i].length), sum(word2[i].length) <= 103
word1[i] and word2[i] consist of lowercase letters.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
        class Solution {
public:
    bool arrayStringsAreEqual(vector<string>& w1, vector<string>& w2) {
        int i=0,ii=0,j=0,jj=0;
        while(i<w1.size() && j<w2.size())
        {
            while(ii<w1[i].size() && jj<w2[j].size())
            {
               if(w1[i][ii] != w2[j][jj]) return 0;
               ii++,jj++;
            }
            if(ii==w1[i].size()) { ii=0; i++; }
            if(jj==w2[j].size()) { jj=0; j++; }
        }
        if(i!=w1.size() || j!=w2.size()) return 0;
        return 1;

    }
};
          
 </pre>

