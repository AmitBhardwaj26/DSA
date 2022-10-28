
<h2><a href="https://leetcode.com/problems/group-anagrams/">49. Group Anagrams</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given an array of strings strs, group the anagrams together. You can return the answer in any order.

An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  strs = ["eat","tea","tan","ate","nat","bat"]
<strong>Output:</strong> [["bat"],["nat","tan"],["ate","eat","tea"]]
</pre>



Constraints:
<pre>
1 <= strs.length <= 104
0 <= strs[i].length <= 100
strs[i] consists of lowercase English letters.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
         
class Solution {
public:
    vector<vector<string>> groupAnagrams(vector<string>& st) {
        unordered_map<string,vector<string>> M;
        for(int i=0;i<st.size();i++)
        {
            string s=st[i];
            sort(begin(s),end(s));
            M[s].push_back(st[i]);// push in map ate[tea,eat ]
        }
        vector<vector<string>> ans;
        for(auto i: M)
        {
            ans.push_back(i.second); // push in ans;
           }
        return ans;
    }
};
          
 </pre>

