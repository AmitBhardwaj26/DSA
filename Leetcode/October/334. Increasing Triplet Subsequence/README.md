
<h2><a href="https://leetcode.com/problems/increasing-triplet-subsequence/">334. Increasing Triplet Subsequence</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given an integer array nums, return true if there exists a triple of indices (i, j, k) such that i < j < k and nums[i] < nums[j] < nums[k]. If no such indices exists, return false.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   nums = [1,2,3,4,5]
<strong>Output:</strong> true
</pre>
<pre>
Any triplet where i < j < k is valid.
  </pre>


Constraints:
<pre>
1 <= nums.length <= 5 * 105
-231 <= nums[i] <= 231 - 1
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
    // logic behind is make three pointers and traverse if fisrt smallest number come put it in 1st when 2nd number come put in 2nd and when got 3rd return 1
class Solution {
public:
    bool increasingTriplet(vector<int>& nums) {
        int mid=INT_MAX,m=INT_MAX;
        for(auto it:nums)
        {
            // cout<<it<<"\n";
            if(it<m) m=it;
            else if(it<mid && m<it) mid=it;
            else if(mid<it) return 1;
        }
        return 0;
    }
};
          
 </pre>

