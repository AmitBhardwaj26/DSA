
<h2><a href="https://leetcode.com/problems/longest-palindrome-by-concatenating-two-letter-words/description/">985. Sum of Even Numbers After Queries</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
You are given an array of strings words. Each element of words consists of two lowercase English letters.

Create the longest possible palindrome by selecting some elements from words and concatenating them in any order. Each element can be selected at most once.

Return the length of the longest palindrome that you can create. If it is impossible to create any palindrome, return 0.

A palindrome is a string that reads the same forward and backward.

 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  words = ["lc","cl","gg"]
<strong>Output:</strong> 6
</pre>
<pre>
 One longest palindrome is "lc" + "gg" + "cl" = "lcggcl", of length 6.
Note that "clgglc" is another longest palindrome that can be created.
After adding 2 to nums[3], the array is [-2,-1,3,6], and the sum of even values is -2 + 6 = 4.
  </pre>
  


Constraints:
<pre>
1 <= words.length <= 105
words[i].length == 2
words[i] consists of lowercase English letters.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
         class Solution {
public:
    int longestPalindrome(vector<string>& w) {
        int count=0;
        unordered_map<string,int> m,m2;
         for(int i=0;i<w.size();i++)
        {
            string s=w[i];
            reverse(s.begin(),s.end());
            if(s==w[i]) {m2[s]++;}
            else m[w[i]]++;
        }
        bool check=0;
        for(auto it: m2)
        { 
            if(it.second%2==0)  count+=it.second;
            else 
            {
                if(check==0) { count++; check=1; }
                count+=it.second-1;
            }

        }

        int ans=count;
        for(auto it : m)
        {
            string s=it.first;
            reverse(s.begin(),s.end());
           if(m.find(s)!=m.end()) ans+=min(m[s],it.second);
        }
        return 2*ans;
    }
};
 </pre>

