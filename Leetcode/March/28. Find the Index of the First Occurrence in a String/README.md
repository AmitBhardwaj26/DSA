
<h2><a href="https://leetcode.com/problems/sum-of-even-numbers-after-queries/">28. Find the Index of the First Occurrence in a String</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given two strings needle and haystack, return the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.

 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   haystack = "sadbutsad", needle = "sad"
<strong>Output:</strong> 0
</pre>
<pre>
Explanation: "sad" occurs at index 0 and 6.
The first occurrence is at index 0, so we return 0.
  </pre>
 

Constraints:
<pre>
1 <= haystack.length, needle.length <= 104
haystack and needle consist of only lowercase English characters.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
         class Solution {
public:
    int strStr(string haystack, string needle) {
        int n=haystack.size(), m=needle.size();
        for(int i=0,j=m;j<=n;j++,i++)
        {
            string s=haystack.substr(i,m);
            //cout<<s<<" ";
            if(s==needle) return i;
        }
        return -1;
    }
};
          
 </pre>

