
<h2><a href="https://leetcode.com/problems/detect-capital/description/">520. Detect Capital</a></h2>
<h3>Easy</h3>
<hr>
<div><p>
We define the usage of capitals in a word to be right when one of the following cases holds:

All letters in this word are capitals, like "USA".
All letters in this word are not capitals, like "leetcode".
Only the first letter in this word is capital, like "Google".
Given a string word, return true if the usage of capitals in it is right.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  word = "USA"
<strong>Output:</strong> true
</pre>



Constraints:
<pre>
1 <= word.length <= 100
word consists of lowercase and uppercase English letters.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
  class Solution {
    public:
        bool detectCapitalUse(string word) {
            bool first=false;
            if(word[0]>='A' && word[0]<='Z' ) first=true;

            if(first)
            {
                bool checkfcfc=true;
                for(int i=1;i<word.size();i++)
                {
                    if(word[i]>='a' && word[i]<='z')
                        {checkfcfc=false; break;}
                }
                if(checkfcfc) return true;
            }
                bool checkfffl=true;
                for(int i=1;i<word.size();i++)
                {
                    if(word[i]>='A' && word[i]<='Z')
                        {checkfffl=false; break;}
                }
                if(checkfffl) return true;
            return false;
        }
    };
          
 </pre>

