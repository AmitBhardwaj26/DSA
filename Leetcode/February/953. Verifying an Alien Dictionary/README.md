
<h2><a href="https://leetcode.com/problems/sum-of-even-numbers-after-queries/">953. Verifying an Alien Dictionary</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
In an alien language, surprisingly, they also use English lowercase letters, but possibly in a different order. The order of the alphabet is some permutation of lowercase letters.

Given a sequence of words written in the alien language, and the order of the alphabet, return true if and only if the given words are sorted lexicographically in this alien language.

 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  words = ["hello","leetcode"], order = "hlabcdefgijkmnopqrstuvwxyz"
<strong>Output:</strong>true
</pre>
<pre>
Explanation:As 'h' comes before 'l' in this language, then the sequence is sorted.
  </pre>
  
Example 2:

Input: nums = [1], queries = [[4,0]]
Output: [0]
 

Constraints:
<pre>
1 <= words.length <= 100
1 <= words[i].length <= 20
order.length == 26
All characters in words[i] and order are English lowercase letters.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 class Solution {
public:
    bool isAlienSorted(vector<string>& words, string order) {
        map<char,char> m;
        for(int i=0;i<order.size();i++)
        {
            m[order[i]]=(char)('a'+i);
        }
        // for(auto it: m) cout<<it.first<<" "<<it.second<<"\n";
        for(int i=1;i<words.size();i++)
        {
            string a=words[i-1],b=words[i];
            for(int j=0;j<a.size();j++) a[j]=m[a[j]];
            for(int j=0;j<b.size();j++) b[j]=m[b[j]];
            // cout<<a<<" " <<b<<"\n";
            if(a>b) return 0;
        }
        return 1;
    }
};
          
 </pre>

