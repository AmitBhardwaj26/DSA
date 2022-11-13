
<h2><a href="https://leetcode.com/problems/reverse-words-in-a-string/description/">151. Reverse Words in a String</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given an input string s, reverse the order of the words.

A word is defined as a sequence of non-space characters. The words in s will be separated by at least one space.

Return a string of the words in reverse order concatenated by a single space.

Note that s may contain leading or trailing spaces or multiple spaces between two words. The returned string should only have a single space separating the words. Do not include any extra spaces.

 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   s = "the sky is blue"
<strong>Output:</strong>  "blue is sky the"
</pre>

  
Input: s = "  hello world  "
Output: "world hello"
Explanation: Your reversed string should not contain leading or trailing spaces.

 

Constraints:
<pre>
1 <= nums.length <= 104
-104 <= nums[i] <= 104
1 <= queries.length <= 104
-104 <= vali <= 104
0 <= indexi < nums.length
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 class Solution {
public:
    string reverseWords(string s) {
       
        string z="",ans="";
        
        for(int i=s.size()-1;i>=0;i--)
        {
            if(s[i]!=' ') z=s[i]+z;
            else if(s[i]==' ' && z.size()>0) { ans+=z+" "; z="" ; }
        }
        
        if(z.size()>0) ans+=z;
        else ans.pop_back();
        return ans;
    }
};
          
 </pre>

