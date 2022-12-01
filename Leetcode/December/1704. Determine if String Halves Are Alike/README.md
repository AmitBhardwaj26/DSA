
<h2><a href="https://leetcode.com/problems/determine-if-string-halves-are-alike/description/">1704. Determine if String Halves Are Alike</a></h2>
<h3>Easy</h3>
<hr>
<div><p>
You are given a string s of even length. Split this string into two halves of equal lengths, and let a be the first half and b be the second half.

Two strings are alike if they have the same number of vowels ('a', 'e', 'i', 'o', 'u', 'A', 'E', 'I', 'O', 'U'). Notice that s contains uppercase and lowercase letters.

Return true if a and b are alike. Otherwise, return false.

 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>    s = "book"
<strong>Output:</strong> true
</pre>
<pre>
a = "bo" and b = "ok". a has 1 vowel and b has 1 vowel. Therefore, they are alike.
  </pre>
  
Input: s = "textbook"
Output: false
Explanation: a = "text" and b = "book". a has 1 vowel whereas b has 2. Therefore, they are not alike.
Notice that the vowel o is counted twice.
 

Constraints:
<pre>
2 <= s.length <= 1000
s.length is even.
s consists of uppercase and lowercase letters.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
   class Solution {
     public:
         bool halvesAreAlike(string s) {
             int count=0;
             int n=s.size()/2;
             for(int i=0;i<n;i++)
             {
                 if(s[i]=='A'||s[i]=='E'||s[i]=='I'||s[i]=='O'||s[i]=='U'||
                 s[i]=='a'||s[i]=='e'||s[i]=='i'||s[i]=='o'||s[i]=='u')
                     count++;
             }
             for(int i=n;i<s.size();i++) 
             {
                 if(s[i]=='A'||s[i]=='E'||s[i]=='I'||s[i]=='O'||s[i]=='U'||
                 s[i]=='a'||s[i]=='e'||s[i]=='i'||s[i]=='o'||s[i]=='u')
                     count--;
             }
             if(count==0) return 1;
             else return 0;
         }
     };
          
 </pre>

