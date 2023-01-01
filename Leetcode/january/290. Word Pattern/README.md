
<h2><a href="https://leetcode.com/problems/word-pattern/description/">985. Sum of Even Numbers After Queries</a></h2>
<h3>Easy</h3>
<hr>
<div><p>
Given a pattern and a string s, find if s follows the same pattern.

Here follow means a full match, such that there is a bijection between a letter in pattern and a non-empty word in s.

 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   pattern = "abba", s = "dog cat cat dog"
<strong>Output:</strong> true
</pre>
<pre>
Explanation: At the beginning, the array is [1,2,3,4].
After adding 1 to nums[0], the array is [2,2,3,4], and the sum of even values is 2 + 2 + 4 = 8.
After adding -3 to nums[1], the array is [2,-1,3,4], and the sum of even values is 2 + 4 = 6.
After adding -4 to nums[0], the array is [-2,-1,3,4], and the sum of even values is -2 + 4 = 2.
After adding 2 to nums[3], the array is [-2,-1,3,6], and the sum of even values is -2 + 6 = 4.
  </pre>
  

 

Constraints:
<pre>
1 <= pattern.length <= 300
pattern contains only lower-case English letters.
1 <= s.length <= 3000
s contains only lowercase English letters and spaces ' '.
s does not contain any leading or trailing spaces.
All the words in s are separated by a single space.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 class Solution {
public:
    bool wordPattern(string s, string s1) {
        
       // string s1[s.size];

        unordered_map<string,int> m;
        unordered_map<int,string> m1;
        
        int i=0,x;
        string z="";
            for(int j=0;j<s1.size();j++)
            {
             if(s1[j]==' ')   
             {
                  x=s[i]-'a';
                if( m.find(z)!=m.end()) 
                  { if(m[z]!=x) return false;}
                  
                else {m[z]=x;}
                 
                if( m1.find(x)!=m1.end()) 
                  { if(m1[x]!=z) return false;}
                  
                else {m1[x]=z;}
                 
                 
                 z=""; i++; if(i==s.size()) return 0;
            } 
                 
                 else { z+=s1[j];  }
            }
         x=s[i]-'a';
        cout<<x<<" "<<z<<"\n";
        if( m.find(z)!=m.end()) 
                  { if(m[z]!=x) return false;}
        if( m1.find(x)!=m1.end()) 
                  { if(m1[x]!=z) return false;}
           if(i!=s.size()-1) return 0;       
        return true;
    }
};
 </pre>

