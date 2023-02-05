
<h2><a href="https://leetcode.com/problems/find-all-anagrams-in-a-string/description/">438. Find All Anagrams in a String</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
 Given two strings s and p, return an array of all the start indices of p's anagrams in s. You may return the answer in any order.

An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   s = "cbaebabacd", p = "abc"
<strong>Output:</strong>  [0,6]
</pre>
<pre>
Explanation: The substring with start index = 0 is "cba", which is an anagram of "abc".
The substring with start index = 6 is "bac", which is an anagram of "abc".
  </pre>
  

Constraints:
<pre>
1 <= s.length, p.length <= 3 * 104
s and p consist of lowercase English letters.
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

