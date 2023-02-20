
<h2><a href="https://leetcode.com/problems/search-insert-position/description/">35. Search Insert Position</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given a sorted array of distinct integers and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You must write an algorithm with O(log n) runtime complexity.

 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   nums = [1,3,5,6], target = 5
<strong>Output:</strong> 2
</pre>


Constraints:
<pre>
1 <= nums.length <= 104
-104 <= nums[i] <= 104
nums contains distinct values sorted in ascending order.
-104 <= target <= 104
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
          class Solution {
public:
    int searchInsert(vector<int>& nums, int target) {
        auto it=lower_bound(nums.begin(),nums.end(),target)-nums.begin();
        return it;
        
    }
};
          
 </pre>

