
<h2><a href="https://leetcode.com/problems/check-if-the-sentence-is-pangram/">1832. Check if the Sentence Is Pangram</a></h2>
<h3>Easy</h3>
<hr>
<div><p>
 A pangram is a sentence where every letter of the English alphabet appears at least once.

Given a string sentence containing only lowercase English letters, return true if sentence is a pangram, or false otherwise.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   sentence = "thequickbrownfoxjumpsoverthelazydog"
<strong>Output:</strong> true
</pre>
<pre>
sentence contains at least one of every letter of the English alphabet.
  </pre>
  


Constraints:
<pre>
1 <= sentence.length <= 1000
sentence consists of lowercase English letters.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 class Solution {
public:
    bool checkIfPangram(string s) {
        int a[26]={0};
        for(int i=0;i<s.size();i++)
            a[s[i]-'a']++;
        for(int i=0;i<26;i++) if(a[i]==0) return 0;
        return 1;

    }
};
          
 </pre>

