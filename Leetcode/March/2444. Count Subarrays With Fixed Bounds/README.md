
<h2><a href="https://leetcode.com/problems/count-subarrays-with-fixed-bounds/description/">2444. Count Subarrays With Fixed Bounds</a></h2>
<h3>Hard</h3>
<hr>
<div><p>
You are given an integer array nums and two integers minK and maxK.

A fixed-bound subarray of nums is a subarray that satisfies the following conditions:

The minimum value in the subarray is equal to minK.
The maximum value in the subarray is equal to maxK.
Return the number of fixed-bound subarrays.

A subarray is a contiguous part of an array.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  nums = [1,3,5,2,7,5], minK = 1, maxK = 5
<strong>Output:</strong> [8,6,2,4]
</pre>
<pre>
Explanation: The fixed-bound subarrays are [1,3,5] and [1,3,5,2].
  </pre>
  

Constraints:
<pre>
2 <= nums.length <= 105
1 <= nums[i], minK, maxK <= 106
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
         class Solution {
public:
        long long countSubarrays(vector<int>& A, int minK, int maxK) {
        long res = 0, jbad = -1, jmin = -1, jmax = -1, n = A.size();
        for (int i = 0; i < n; ++i) {
            if (A[i] < minK || A[i] > maxK) jbad = i;
            if (A[i] == minK) jmin = i;
            if (A[i] == maxK) jmax = i;
            res += max(0L, min(jmin, jmax) - jbad);
        }
        return res;
    }
};
          
 </pre>

