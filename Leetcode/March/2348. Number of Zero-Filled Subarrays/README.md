
<h2><a href="https://leetcode.com/problems/sum-of-even-numbers-after-queries/">2348. Number of Zero-Filled Subarrays</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given an integer array nums, return the number of subarrays filled with 0.

A subarray is a contiguous non-empty sequence of elements within an array.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   nums = [1,3,0,0,2,0,0,4]
<strong>Output:</strong> 6
</pre>
<pre>
Explanation: There are 4 occurrences of [0] as a subarray.
There are 2 occurrences of [0,0] as a subarray.
There is no occurrence of a subarray with a size more than 2 filled with 0. Therefore, we return 6.
  </pre>

 

Constraints:
<pre>
1 <= nums.length <= 105
-109 <= nums[i] <= 109
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
   class Solution {
public:
    long long zeroFilledSubarray(vector<int>& nums) {
        long long ans=0,count=0;
        for(int i=0;i<nums.size();i++)
        {
           
               if(nums[i]==0)
               {
                  count++;
                  ans+=count;
                  //cout<<ans<<" ";
               }
             else count=0;
           
        }
        return ans;
    }
};
 </pre>

