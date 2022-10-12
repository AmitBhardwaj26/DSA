
<h2><a href="https://leetcode.com/problems/largest-perimeter-triangle/description/">976. Largest Perimeter Triangle</a></h2>
<h3>Easy</h3>
<hr>
<div><p>
Given an integer array nums, return the largest perimeter of a triangle with a non-zero area, formed from three of these lengths. If it is impossible to form any triangle of a non-zero area, return 0.

 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   nums = [2,1,2]
<strong>Output:</strong> 5
</pre>


Constraints:
<pre>
3 <= nums.length <= 104
1 <= nums[i] <= 106
</pre>
  
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
         class Solution {
public:
    int largestPerimeter(vector<int>& nums) {
        sort(nums.begin(),nums.end());
        for(int i=nums.size()-1;i>=2;i--)
        {
            if(nums[i]<(nums[i-1]+nums[i-2])) 
                return nums[i]+nums[i-1]+nums[i-2];
        }
        return 0;
    }
    
};
          
 </pre>

