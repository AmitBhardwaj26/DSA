
<h2><a href="https://leetcode.com/problems/house-robber/description/">198. House Robber</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security systems connected and it will automatically contact the police if two adjacent houses were broken into on the same night.

Given an integer array nums representing the amount of money of each house, return the maximum amount of money you can rob tonight without alerting the police.

 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> nums = [1,2,3,1]
<strong>Output:</strong> 4
</pre>
<pre>
Rob house 1 (money = 1) and then rob house 3 (money = 3).
Total amount you can rob = 1 + 3 = 4.
  </pre>
  
Input: nums = [2,7,9,3,1]
Output: 12
Explanation: Rob house 1 (money = 2), rob house 3 (money = 9) and rob house 5 (money = 1).
Total amount you can rob = 2 + 9 + 1 = 12.

Constraints:
<pre>
1 <= nums.length <= 100
0 <= nums[i] <= 400
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
        class Solution {
public:
    int rob(vector<int>& nums) {
        long a=0,b=0;
        if(nums.size()==1) return nums[0];
        else 
        {
            nums[1]= max(nums[0],nums[1]);
            if(nums.size()==2) { return nums[1];}
        
        
            for(int i=2;i<nums.size();i++)
            {
                nums[i]=max((nums[i-2]+nums[i]),nums[i-1]);
            }
            return nums[nums.size()-1];
        }
    }
};
          
 </pre>

