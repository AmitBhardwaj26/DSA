
<h2><a href="https://leetcode.com/problems/contains-duplicate-ii/">219. Contains Duplicate II</a></h2>
<h3>Easy</h3>
<hr>
<div><p>
 Given an integer array nums and an integer k, return true if there are two distinct indices i and j in the array such that nums[i] == nums[j] and abs(i - j) <= k.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   nums = [1,2,3,1], k = 3
<strong>Output:</strong> true
</pre>

Input: nums = [1,0,1,1], k = 1
Output: true
Constraints:
<pre>
1 <= nums.length <= 105
-109 <= nums[i] <= 109
0 <= k <= 105
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
class Solution {
 public:
    bool containsNearbyDuplicate(vector<int>& nums, int k) {
     vector<pair<int,int>> v;
        for(int i=0;i<nums.size();i++)
        {
            v.push_back({nums[i],i});
        }
        sort(v.begin(),v.end());
        
        for(int i=1;i<nums.size();i++)
        {
            if(v[i-1].first==v[i].first && abs(v[i-1].second-v[i].second)<=k) {return true;}
            
        }
        return false;
    }
};
          
 </pre>

