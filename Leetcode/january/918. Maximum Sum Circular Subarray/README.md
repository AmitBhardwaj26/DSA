
<h2><a href="https://leetcode.com/problems/maximum-sum-circular-subarray/description/">918. Maximum Sum Circular Subarray</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given a circular integer array nums of length n, return the maximum possible sum of a non-empty subarray of nums.

A circular array means the end of the array connects to the beginning of the array. Formally, the next element of nums[i] is nums[(i + 1) % n] and the previous element of nums[i] is nums[(i - 1 + n) % n].

A subarray may only include each element of the fixed buffer nums at most once. Formally, for a subarray nums[i], nums[i + 1], ..., nums[j], there does not exist i <= k1, k2 <= j with k1 % n == k2 % n.

 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   nums = [1,-2,3,-2]
<strong>Output:</strong> 3
</pre>

  
 

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
 
        // logic behind this is simple subtract most consecutive negative subarray sum using kadane algo to total sum or ans will be maximux subarray sum in consecutive 

// kadane algo take 2 variable maxmum sum, sum at each index maxsum=max(maxsum,sum) and is sum<0 then sum=0;

class Solution {
public:
    int maxSubarraySumCircular(vector<int>& nums) {
        int sum=0;
        int maxi=INT_MIN,tempmaxi=0,mini=INT_MAX,tempmini=0;
        for(int i=0;i<nums.size();i++)
        {
            sum+=nums[i];
            tempmaxi+=nums[i];  maxi=max(maxi,tempmaxi);
            if(tempmaxi<0) tempmaxi=0;
             tempmini+=nums[i]; mini=min(mini,tempmini);
            if(tempmini>0) tempmini=0;
        }
        if(sum==mini) return maxi;
        return max(maxi,sum-mini);
    }
};
          
 </pre>

