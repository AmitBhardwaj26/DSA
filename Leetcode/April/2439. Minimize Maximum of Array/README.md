
<h2><a href="https://leetcode.com/problems/minimize-maximum-of-array/description/">2439. Minimize Maximum of Array</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
You are given a 0-indexed array nums comprising of n non-negative integers.

In one operation, you must:

Choose an integer i such that 1 <= i < n and nums[i] > 0.
Decrease nums[i] by 1.
Increase nums[i - 1] by 1.
Return the minimum possible value of the maximum integer of nums after performing any number of operations.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   nums = [3,7,1,6]
<strong>Output:</strong>  5
</pre>
<pre>
Explanation: One set of optimal operations is as follows:
1. Choose i = 1, and nums becomes [4,6,1,6].
2. Choose i = 3, and nums becomes [4,6,2,5].
3. Choose i = 1, and nums becomes [5,5,2,5].
The maximum integer of nums is 5. It can be shown that the maximum number cannot be less than 5.
Therefore, we return 5.
  </pre>
  
Example 2:

Input: nums = [1], queries = [[4,0]]
Output: [0]
 

Constraints:
<pre>
n == nums.length
2 <= n <= 105
0 <= nums[i] <= 109
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 class Solution {
public:
    int minimizeArrayValue(vector<int>& nums) {
        long long int ans=0,s=0;
        for(int i=0;i<nums.size();i++){
            s+=nums[i];
            ans=max(ans,(s+i)/(i+1));
        }
        return ans;
    }
};   
 </pre>

