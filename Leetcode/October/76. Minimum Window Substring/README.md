
<h2><a href="https://leetcode.com/problems/minimum-window-substring/">76. Minimum Window Substring</a></h2>
<h3>Hard</h3>
<hr>
<div><p>
Given two strings s and t of lengths m and n respectively, return the minimum window substring of s such that every character in t (including duplicates) is included in the window. If there is no such substring, return the empty string "".

The testcases will be generated such that the answer is unique.

A substring is a contiguous sequence of characters within the string.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>    s = "ADOBECODEBANC", t = "ABC"
<strong>Output:</strong>  "BANC"
</pre>
<pre>
The minimum window substring "BANC" includes 'A', 'B', and 'C' from string t.
  </pre>
  

Constraints:
<pre>
m == s.length
n == t.length
1 <= m, n <= 105
s and t consist of uppercase and lowercase English letters.
 
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
        class Solution {
public:

    string minWindow(string str, string pat) {
           
    int len1 = str.length();
    int len2 = pat.length();
        
     const int no_of_chars = 256;

    if (len1 < len2) {
        return "";
    }

    int hash_pat[no_of_chars] = { 0 };
    int hash_str[no_of_chars] = { 0 };

    
    for (int i = 0; i < len2; i++)
        hash_pat[pat[i]]++;

    int start = 0, start_index = -1, min_len = INT_MAX;

   
    int count = 0; 
    for (int j = 0; j < len1; j++) {
      
        
        hash_str[str[j]]++;

        
        if (hash_str[str[j]] <= hash_pat[str[j]])
            count++;

        if (count == len2) {
          
            while (hash_str[str[start]]
                       > hash_pat[str[start]]
                   || hash_pat[str[start]] == 0) {

                if (hash_str[str[start]]
                    > hash_pat[str[start]])
                    hash_str[str[start]]--;
                start++;
            }

            int len_window = j - start + 1;
            if (min_len > len_window) {
                min_len = len_window;
                start_index = start;
            }
        }
    }


    if (start_index == -1) {
     
        return "";
    }

    
    return str.substr(start_index, min_len);
    }
};
          
 </pre>

