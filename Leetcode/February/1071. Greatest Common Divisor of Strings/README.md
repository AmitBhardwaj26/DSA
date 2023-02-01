
<h2><a href="https://leetcode.com/problems/sum-of-even-numbers-after-queries/">1071. Greatest Common Divisor of Strings</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
For two strings s and t, we say "t divides s" if and only if s = t + ... + t (i.e., t is concatenated with itself one or more times).

Given two strings str1 and str2, return the largest string x such that x divides both str1 and str2.

 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   str1 = "ABCABC", str2 = "ABC"
<strong>Output:</strong>  "ABC"
</pre>


Constraints:
<pre>
1 <= str1.length, str2.length <= 1000
str1 and str2 consist of English uppercase letters.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 // class Solution {
// public:
//     string gcdOfStrings(string str1, string str2) {
//         int m1[26]={0},m2[26]={0};
//         for(int i=0;i<str1.size();i++)            m1[str1[i]-'A']++;
//         for(int i=0;i<str2.size();i++)            m2[str2[i]-'A']++;
        
//         int count=0;
//         for(int i=0;i<26;i++) 
//         {
//             if((m1[i]+m2[i])>0 && (m1[i]==0 || m2[i]==0)) return "";
//           m1[i]= __gcd(m1[i],m2[i]);
//           count+=m1[i];
//         }
//          string s=str1.substr(0,count);
//          for(int i=1;i<(str1.size()/count);i++)
//          {
//              if(str1.substr(count*i,count)!=s) return "";
//          }
//          for(int i=1;i<str2.size()/count;i++)
//          {
//              if(str2.substr(count*i,count)!=s) return "";
//          }
//          return s;
        
//     }
// };
class Solution {
public:
    string gcdOfStrings(string str1, string str2) {
        if(str1+str2 != str2+str1) return "";
        return str1.substr(0,gcd(str1.length(),str2.length()));
    }
};
 </pre>

