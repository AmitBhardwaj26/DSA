
<h2><a href="https://leetcode.com/problems/maximum-number-of-vowels-in-a-substring-of-given-length/description/">1456. Maximum Number of Vowels in a Substring of Given Length</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given a string s and an integer k, return the maximum number of vowel letters in any substring of s with length k.

Vowel letters in English are 'a', 'e', 'i', 'o', and 'u'.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>    s = "abciiidef", k = 3
<strong>Output:</strong> 3
</pre>
<pre>
Explanation: The substring "iii" contains 3 vowel letters.
  </pre>
  

Constraints:
<pre>
1 <= s.length <= 105
s consists of lowercase English letters.
1 <= k <= s.length
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
          class Solution {
          public:
              vector<int> sumEvenAfterQueries(vector<int>& nums, vector<vector<int>>& q) {
                  int ans=0;
                  for(int i=0;i<nums.size();i++)
                  {
                      if(nums[i]%2==0) ans+=nums[i];
                  }
                  vector<int> v;
                  for(int i=0;i<q.size();i++)
                  {
                      int val=q[i][0],ind=q[i][1];
                      if(nums[ind]%2==0) ans-=nums[ind];
                      nums[ind]+=val;
                      if(nums[ind]%2==0) ans+=nums[ind];
                      v.push_back(ans);
                  }
                  return v;
              }
          };
          
 </pre>

