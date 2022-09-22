
<h2><a href="https://leetcode.com/problems/reverse-words-in-a-string-iii/">557.Reverse Words in a String III</a></h2>
<h3>Easy</h3>
<hr>
<div><p>
  Given a string s, reverse the order of characters in each word within a sentence while still preserving whitespace and initial word order.

 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   s = "Let's take LeetCode contest"
<strong>Output:</strong> "s'teL ekat edoCteeL tsetnoc"
</pre>


<h3>Constraints:</h3>
<pre>
1 <= s.length <= 5 * 104
s contains printable ASCII characters.
s does not contain any leading or trailing spaces.
There is at least one word in s.
All the words in s are separated by a single space.
</pre>

  <hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>

    class Solution {
     public:
        string reverseWords(string s) {
            int j=0,i=0;
           for(i=0;i<s.size();i++)
           {
               if(s[i]==' ') { reverse(s.begin()+j,s.begin()+i); j=i+1;}
           }
            reverse(s.begin()+j,s.begin()+i); 
            return s;
        }
    };
    
 </pre>

