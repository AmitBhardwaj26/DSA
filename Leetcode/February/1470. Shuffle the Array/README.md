
<h2><a href="https://leetcode.com/problems/shuffle-the-array/description/">1470. Shuffle the Array</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given the array nums consisting of 2n elements in the form [x1,x2,...,xn,y1,y2,...,yn].

Return the array in the form [x1,y1,x2,y2,...,xn,yn].
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   nums = [2,5,1,3,4,7], n = 3
<strong>Output:</strong> [2,3,5,4,1,7] 
</pre>
<pre>
Explanation:  Since x1=2, x2=5, x3=1, y1=3, y2=4, y3=7 then the answer is [2,3,5,4,1,7].
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

