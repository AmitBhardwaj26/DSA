
<h2><a href="https://leetcode.com/problems/sum-of-even-numbers-after-queries/">974. Subarray Sums Divisible by K</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given an integer array nums and an integer k, return the number of non-empty subarrays that have a sum divisible by k.

A subarray is a contiguous part of an array.

 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  nums = [4,5,0,-2,-3,1], k = 5
<strong>Output:</strong> 7
</pre>
<pre>
Explanation: There are 7 subarrays with a sum divisible by k = 5:
[4, 5, 0, -2, -3, 1], [5], [5, 0], [5, 0, -2, -3], [0], [0, -2, -3], [-2, -3]
  </pre>
  
Example 2:

Input: nums = [1], queries = [[4,0]]
Output: [0]
 

Constraints:
<pre>
1 <= nums.length <= 104
-104 <= nums[i] <= 104
1 <= queries.length <= 104
-104 <= vali <= 104
0 <= indexi < nums.length
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
          class Solution {
public:
    int subarraysDivByK(vector<int>& nums, int k) {
        map<int,int> m;
        int ans=0,sum=0;
        for(int i=0;i<nums.size();i++)
        {
            if(nums[i]<0) { nums[i]=k-abs(nums[i])%k;  }
           sum+=nums[i]; 
           sum%=k;
           if(sum==0) ans++;
           ans+=m[sum];
           m[sum]++;
        }
      
        return ans;
    }
};
          
 </pre>

