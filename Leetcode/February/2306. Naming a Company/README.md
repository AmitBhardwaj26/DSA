
<h2><a href="https://leetcode.com/problems/naming-a-company/description/">2306. Naming a Company</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
You are given an array of strings ideas that represents a list of names to be used in the process of naming a company. The process of naming a company is as follows:

Choose 2 distinct names from ideas, call them ideaA and ideaB.
Swap the first letters of ideaA and ideaB with each other.
If both of the new names are not found in the original ideas, then the name ideaA ideaB (the concatenation of ideaA and ideaB, separated by a space) is a valid company name.
Otherwise, it is not a valid name.
Return the number of distinct valid names for the company.

 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> ideas = ["coffee","donuts","time","toffee"]
<strong>Output:</strong> 6
</pre>
<pre>
Explanation:The following selections are valid:
- ("coffee", "donuts"): The company name created is "doffee conuts".
- ("donuts", "coffee"): The company name created is "conuts doffee".
- ("donuts", "time"): The company name created is "tonuts dime".
- ("donuts", "toffee"): The company name created is "tonuts doffee".
- ("time", "donuts"): The company name created is "dime tonuts".
- ("toffee", "donuts"): The company name created is "doffee tonuts".
Therefore, there are a total of 6 distinct company names.

The following are some examples of invalid selections:
- ("coffee", "time"): The name "toffee" formed after swapping already exists in the original array.
- ("time", "toffee"): Both names are still the same after swapping and exist in the original array.
- ("coffee", "toffee"): Both names formed after swapping already exist in the original array.
  </pre>
  
 

Constraints:
<pre>
2 <= ideas.length <= 5 * 104
1 <= ideas[i].length <= 10
ideas[i] consists of lowercase English letters.
All the strings in ideas are unique.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
        //Optimized code - O(n*m) and O(26*n) space
class Solution {
public:
    long long distinctNames(vector<string>& ideas) {
        long long disName = 0;
        vector<unordered_set<string>> arr(26);
        for (string s : ideas) 
            arr[s[0] - 'a'].insert(s.substr(1));
        
        for (int i = 0; i < 25; i++) {
            for (int j = i + 1; j < 26; j++) {
                unordered_set<string> set;
                set.insert(arr[i].begin(), arr[i].end());
                set.insert(arr[j].begin(), arr[j].end());
                disName += (arr[i].size() - set.size()) * (arr[j].size() - set.size());
            }
        }
        return disName * 2;
    }
};
          
 </pre>

