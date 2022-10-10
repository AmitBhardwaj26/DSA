
<h2><a href="https://leetcode.com/problems/break-a-palindrome/description/">1328. Break a Palindrome</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given a palindromic string of lowercase English letters palindrome, replace exactly one character with any lowercase English letter so that the resulting string is not a palindrome and that it is the lexicographically smallest one possible.

Return the resulting string. If there is no way to replace a character to make it not a palindrome, return an empty string.

A string a is lexicographically smaller than a string b (of the same length) if in the first position where a and b differ, a has a character strictly smaller than the corresponding character in b. For example, "abcc" is lexicographically smaller than "abcd" because the first position they differ is at the fourth character, and 'c' is smaller than 'd'.
  </p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   palindrome = "abccba"
<strong>Output:</strong> "aaccba"
</pre>
<pre>
There are many ways to make "abccba" not a palindrome, such as "zbccba", "aaccba", and "abacba".
Of all the ways, "aaccba" is the lexicographically smallest.
</pre>
  


Constraints:
<pre>
1 <= palindrome.length <= 1000
palindrome consists of only lowercase English letters.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
    //case 1: length is 1
//case 2: ab...ba replace b with with a
//case 3: aabab then abb
//case 3: aaa last a with b
//both in case 2 and 3 replace last one

class Solution {
public:
    string breakPalindrome(string p) {
        //case 1
        if(p.size()==1) return "";
          int n=p.size(), arr[26]={0};
          for(int i=0;i<n;i++) arr[p[i]-'a']++;
          if(arr[0]<n-1) 
          {
              for(int i=0;i<n;i++)
               {if(p[i]!='a') {p[i]='a'; break;}}
          }
          else p[n-1]='b';
          return p;
    }
};   
 </pre>

