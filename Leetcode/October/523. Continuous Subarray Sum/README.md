
<h2><a href="https://leetcode.com/problems/continuous-subarray-sum/description/">523. Continuous Subarray Sum</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given an integer array nums and an integer k, return true if nums has a continuous subarray of size at least two whose elements sum up to a multiple of k, or false otherwise.

An integer x is a multiple of k if there exists an integer n such that x = n * k. 0 is always a multiple of k.

 
</p>

Input: nums = [23,2,4,6,7], k = 6
Output: true
Explanation: [2, 4] is a continuous subarray of size 2 whose elements sum up to 6.
  
Example 2:

Input: nums = [1], queries = [[4,0]]
Output: [0]
 

Constraints:
<pre>
1 <= nums.length <= 105
0 <= nums[i] <= 109
0 <= sum(nums[i]) <= 231 - 1
1 <= k <= 231 - 1
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
         class Solution {
                 public:
                     bool checkSubarraySum(vector<int>& nums, int k) {
                         int n=nums.size();
                         long long pre[100001]={0};
                         pre[0]=nums[0];
                         for(int i=1;i<n;i++) pre[i]=nums[i]+pre[i-1];
                         map<long long,int> m;
                         int temp=k-(nums[0]%k);
                         for(int i=1;i<n;i++)
                         {
                             if(pre[i]%k==0) { return 1;}
                             int x=k-(pre[i]%k);
                             if(m[x]==1) {  return 1;}
                             m[temp]=1;
                             temp=k- (pre[i]%k);
                         }
                       return 0;
                     }
                 };
          
 </pre>

