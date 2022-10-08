
<h2><a href="https://leetcode.com/problems/3sum-closest/">16. 3Sum Closest</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given an integer array nums of length n and an integer target, find three integers in nums such that the sum is closest to target.

Return the sum of the three integers.

You may assume that each input would have exactly one solution.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  nums = [-1,2,1,-4], target = 1
<strong>Output:</strong> 2
</pre>
<pre>
Explanation: The sum that is closest to the target is 2. (-1 + 2 + 1 = 2).
  </pre>
  


Constraints:
<pre>
3 <= nums.length <= 1000
-1000 <= nums[i] <= 1000
-104 <= target <= 104
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 class Solution {
public:
    int threeSumClosest(vector<int>& nums, int tar) {
        sort(nums.begin(),nums.end());
        int ans=0,com=INT_MAX,i=0,n=nums.size();
        while(i < n-1)
        {
            int j=i+1,k=n-1;
            while(j < k)
            {
               int tsum=nums[i]+nums[j]+nums[k];
               if(abs(tar-tsum) < com)
               {
                   com=abs(tar-tsum);
                   ans=tsum;
               
               }
               if(tsum > tar) k--;
               else j++;
            }
            i++;
        }
        return ans;
    }
};
          
 </pre>

