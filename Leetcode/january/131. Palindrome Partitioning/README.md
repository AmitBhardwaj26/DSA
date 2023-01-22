
<h2><a href="https://leetcode.com/problems/sum-of-even-numbers-after-queries/">985. Sum of Even Numbers After Queries</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given a string s, partition s such that every 
substring
 of the partition is a 
palindrome
. Return all possible palindrome partitioning of s.
 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   s = "aab"
<strong>Output:</strong> [["a","a","b"],["aa","b"]]
</pre>


Constraints:
<pre>
1 <= s.length <= 16
s contains only lowercase English letters.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
        class Solution {
public:
   vector<vector<string>> ans;
   bool pail(string s)
   {
       int i=0,j=s.size()-1;
       while(i<j)
       {
           if(s[i]!=s[j]) return 0;
           i++,j--;
       }
       return 1;
   }

   void solve(int i, string s,vector<string> a)
   {
       //base case 
       if(i>=s.size()) 
       {
           ans.push_back(a);
           return ;
       }
       // choce diagram
       string temp="";
       for(int j=i;j<s.size();j++)
       {
           temp+=s[j];
           if(pail(temp)) 
           {
               a.push_back(temp);
               solve(j+1,s,a);
               a.pop_back();
           }
       }
      
   }
    vector<vector<string>> partition(string s) {
        solve(0,s,vector<string>());
        return ans;
    }
};
          
 </pre>

