
<h2><a href="https://leetcode.com/problems/sort-an-array/description/">912. Sort an Array</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given an array of integers nums, sort the array in ascending order and return it.

You must solve the problem without using any built-in functions in O(nlog(n)) time complexity and with the smallest space complexity possible.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   nums = [5,2,3,1]
<strong>Output:</strong> [1,2,3,5]
</pre>
<pre>
Explanation: After sorting the array, the positions of some numbers are not changed (for example, 2 and 3), while the positions of other numbers are changed (for example, 1 and 5).
  </pre>
 

Constraints:
<pre>
1 <= nums.length <= 5 * 104
-5 * 104 <= nums[i] <= 5 * 104
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
        class Solution {
public:
    vector<int> sortArray(vector<int>& nums) {
      sort(nums.begin(),nums.end());
      return nums;
    }
};
          
 </pre>

