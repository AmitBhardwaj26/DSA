
<h2><a href="https://leetcode.com/problems/sum-of-even-numbers-after-queries/">1822. Sign of the Product of an Array</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
There is a function signFunc(x) that returns:

1 if x is positive.
-1 if x is negative.
0 if x is equal to 0.
You are given an integer array nums. Let product be the product of all values in the array nums.

Return signFunc(product).
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   nums = [-1,-2,-3,-4,3,2,1]
<strong>Output:</strong> 1
</pre>
<pre>
Explanation: The product of all values in the array is 144, and signFunc(144) = 1
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
    int arraySign(vector<int>& nums) {
        int minus=0;
        for(int i=0;i<nums.size();i++)
        {
            if(nums[i]==0) return 0;
            if(nums[i]<0) minus++;
        }
        if(minus%2==0) return 1;
        return -1;
    }
};
 </pre>

