
<h2><a href="https://leetcode.com/problems/permutation-in-string/description/">567. Permutation in String</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
 You are given an integer array nums and an array queries where queries[i] = [vali, indexi].

For each query i, first, apply nums[indexi] = nums[indexi] + vali, then print the sum of the even values of nums.

Return an integer array answer where answer[i] is the answer to the ith query.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   s1 = "ab", s2 = "eidbaooo"
<strong>Output:</strong>  true
</pre>
<pre>
Explanation: s2 contains one permutation of s1 ("ba").
  </pre>
  


Constraints:
<pre>
1 <= s1.length, s2.length <= 104
s1 and s2 consist of lowercase English letters.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
  class Solution {
   public:
       bool checkInclusion(string s1, string s2) {
          if(s1.size()==0 || s2.size()==0 || s1.size()>s2.size()) return false;

           long long a=0;
           sort(s1.begin(),s1.end());
           int l1=s1.size();
           for(int i=0;i<l1;i++)   a+=pow(s1[i],3);

           long long b=0;
           for(int i=0;i<l1;i++)    b+=pow(s2[i],3);

           if(a==b) return true;
           for(int i=l1;i<s2.size();i++)
           {
               b+=pow(s2[i],3)-pow(s2[i-l1],3);
               if(a==b) return true;
           }
           return false;

       }
};
          
 </pre>

