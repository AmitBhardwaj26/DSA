
<h2><a href="https://leetcode.com/problems/binary-search/description/">704. Binary Search</a></h2>
<h3>Easy</h3>
<hr>
<div><p>
 Given an array of integers nums which is sorted in ascending order, and an integer target, write a function to search target in nums. If target exists, then return its index. Otherwise, return -1.

You must write an algorithm with O(log n) runtime complexity.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  nums = [-1,0,3,5,9,12], target = 9
<strong>Output:</strong> 4
</pre>
<pre>
Explanation: 9 exists in nums and its index is 4
  </pre>
  
Example 2:

Input: nums = [1], queries = [[4,0]]
Output: [0]
 

Constraints:
<pre>
1 <= nums.length <= 104
-104 < nums[i], target < 104
All the integers in nums are unique.
nums is sorted in ascending order.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 class Solution {
public:
    int search(vector<int>& nums, int target) {
        int i=0,j=nums.size()-1, mid;
        while(i<=j)
        {
            mid=(i+j)/2;
            if(nums[mid]==target) return mid;
            else if(nums[mid]<target) i=mid+1;
            else j=mid-1;
        }
        return -1;
    }
};
 </pre>

