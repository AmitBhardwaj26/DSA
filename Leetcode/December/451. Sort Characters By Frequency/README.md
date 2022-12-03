
<h2><a href="https://leetcode.com/problems/sort-characters-by-frequency/">451. Sort Characters By Frequency</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given a string s, sort it in decreasing order based on the frequency of the characters. The frequency of a character is the number of times it appears in the string.

Return the sorted string. If there are multiple answers, return any of them.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  s = "tree"
<strong>Output:</strong>  "eert"
</pre>
<pre>
'e' appears twice while 'r' and 't' both appear once.
So 'e' must appear before both 'r' and 't'. Therefore "eetr" is also a valid answer.
  </pre>
  


Constraints:
<pre>
1 <= s.length <= 5 * 105
s consists of uppercase and lowercase English letters and digits.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
        //Step1: Store the frequency of each character in unordered map 
//Step2: Push the frequency,character in vector of pair
//Step3: Sort the vector 
//Step4: Traverse from the right, Append the character w.r.t their frequency into answer string    
class Solution {
public:
    string frequencySort(string s) {
        unordered_map<char,int> m;
        for(int i=0;i<s.size();i++)
        {
            m[s[i]]++;
        }
        vector<pair<int,char>> v;
        for(auto it : m)    v.push_back({it.second,it.first});
        
        sort(v.begin(),v.end());
        s="";
        for(int i=v.size()-1;i>=0;i--)
        {
           int x=v[i].first;
           char c=v[i].second; 
           while(x>0)
           {
               s+=c; x--;
           }    
        }
        return s;
    }
};
          
 </pre>

