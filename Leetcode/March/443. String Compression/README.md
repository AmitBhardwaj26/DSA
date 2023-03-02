
<h2><a href="https://leetcode.com/problems/string-compression/description/">443. String Compression</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given an array of characters chars, compress it using the following algorithm:

Begin with an empty string s. For each group of consecutive repeating characters in chars:

If the group's length is 1, append the character to s.
Otherwise, append the character followed by the group's length.
The compressed string s should not be returned separately, but instead, be stored in the input character array chars. Note that group lengths that are 10 or longer will be split into multiple characters in chars.

After you are done modifying the input array, return the new length of the array.

You must write an algorithm that uses only constant extra space.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   chars = ["a","a","b","b","c","c","c"]
<strong>Output:</strong> Return 6, and the first 6 characters of the input array should be: ["a","2","b","2","c","3"]
</pre>
<pre>
Explanation: The groups are "aa", "bb", and "ccc". This compresses to "a2b2c3".
  </pre>
  

 

Constraints:
<pre>
1 <= chars.length <= 2000
chars[i] is a lowercase English letter, uppercase English letter, digit, or symbol.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 class Solution {
public:
    int compress(vector<char>& chars) {
        int n = chars.size();
        if (n == 1) {
            return 1;
        }
        
        int i = 0, j = 0;
        while (i < n) {
            int count = 1;
            while (i < n - 1 && chars[i] == chars[i + 1]) {
                count++;
                i++;
            }
            
            chars[j++] = chars[i++];
            if (count > 1) {
                string countStr = to_string(count);
                for (char c : countStr) {
                    chars[j++] = c;
                }
            }
        }
        
        return j;
    }
};
 </pre>

