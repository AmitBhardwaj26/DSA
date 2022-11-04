
<h2><a href="https://leetcode.com/problems/sum-of-even-numbers-after-queries/">985. Sum of Even Numbers After Queries</a></h2>
<h3>Easy</h3>
<hr>
<div><p>
Given a string s, reverse only all the vowels in the string and return it.

The vowels are 'a', 'e', 'i', 'o', and 'u', and they can appear in both lower and upper cases, more than once.

 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  s = "leetcode"
<strong>Output:</strong>  "leotcede"
</pre>

Constraints:
<pre>
1 <= s.length <= 3 * 105
s consist of printable ASCII characters.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
        class Solution {
                public:
                    bool isvowel(char c)
                    {
                        if(c=='a' || c=='e' || c=='i' || c=='o' || c=='u') return 1;
                        else if(c=='A' || c=='E' || c=='I' || c=='O' || c=='U') return 1;
                        return 0;
                    }
                    string reverseVowels(string s) {
                        int i=0,j=s.size()-1;
                        while(i < j)
                        {
                            while(i < s.size() and !isvowel(s[i])) i++;
                            while(j >=0 and !isvowel(s[j])) j--;
                           if(i < j) {
                               char temp=s[i]; s[i]=s[j]; s[j]=temp;
                           }
                           i++,j--;
                        }
                        return s;
                    }
                };
        
 </pre>

