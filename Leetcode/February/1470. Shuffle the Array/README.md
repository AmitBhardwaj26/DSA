
<h2><a href="https://leetcode.com/problems/shuffle-the-array/description/">1470. Shuffle the Array</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given the array nums consisting of 2n elements in the form [x1,x2,...,xn,y1,y2,...,yn].

Return the array in the form [x1,y1,x2,y2,...,xn,yn].
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   nums = [1,2,3,4], queries = [[1,0],[-3,1],[-4,0],[2,3]]
<strong>Output:</strong> [8,6,2,4]
</pre>
<pre>
Explanation: At the beginning, the array is [1,2,3,4].
After adding 1 to nums[0], the array is [2,2,3,4], and the sum of even values is 2 + 2 + 4 = 8.
After adding -3 to nums[1], the array is [2,-1,3,4], and the sum of even values is 2 + 4 = 6.
After adding -4 to nums[0], the array is [-2,-1,3,4], and the sum of even values is -2 + 4 = 2.
After adding 2 to nums[3], the array is [-2,-1,3,6], and the sum of even values is -2 + 6 = 4.
  </pre>
  

 

Constraints:
<pre>
1 <= n <= 500
nums.length == 2n
1 <= nums[i] <= 10^3
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
      class Solution {
public:
    vector<int> shuffle(vector<int>& nums, int n) {
        vector<int> v;
        for(int i=0;i<n;i++)
        {
            v.push_back(nums[i]);
        }
        int i=0, j=n,k=0;
        for(int i=0;i<n;i++,j++)
        {
            nums[k++]=v[i];
            nums[k++]=nums[j];
        }
        return nums;
    }
};
          
 </pre>

